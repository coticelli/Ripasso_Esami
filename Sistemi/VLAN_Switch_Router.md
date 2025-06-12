# 🔗 Implementazione VLAN, Switch MultiLayer e Router on a stick

La comunicazione tra VLAN diverse richiede un dispositivo di livello 3 (Rete) che possa instradare (routare) il traffico tra di esse. Le due tecniche più comuni per farlo sono il "Router on a Stick" e l'uso di uno Switch Multilayer.

---

## 📍 Scenario di Partenza

*   Abbiamo uno switch con diverse porte configurate su VLAN separate (es. VLAN 10 per le Vendite, VLAN 20 per la Contabilità).
*   **Problema:** Un dispositivo nella VLAN 10 non può comunicare con un dispositivo nella VLAN 20, perché si trovano in domini di broadcast e sottoreti IP diverse.

---

## 1. Tecnica "Router on a Stick"

*   **Concetto:** Si utilizza un singolo router, collegato allo switch tramite un'unica interfaccia fisica. Questa interfaccia del router viene configurata come **trunk** e suddivisa in più **sotto-interfacce logiche (sub-interfaces)**, una per ogni VLAN.
*   **Come funziona:**
    1.  Il traffico che da un PC nella VLAN 10 deve raggiungere la VLAN 20, viene inviato allo switch.
    2.  Lo switch, vedendo che la destinazione è in un'altra VLAN, inoltra il frame sulla porta di trunk verso il router, **taggandolo** con l'ID della VLAN di origine (VLAN 10).
    3.  Il router riceve il frame sulla sua sotto-interfaccia configurata per la VLAN 10.
    4.  Il router "spoglia" il frame del tag, analizza il pacchetto IP, vede che la destinazione è nella sottorete della VLAN 20 e lo inoltra alla sotto-interfaccia corrispondente.
    5.  Prima di inviarlo di nuovo allo switch, il router **tagga** il frame con il nuovo ID VLAN (VLAN 20).
    6.  Lo switch riceve il frame taggato e lo inoltra alla porta corretta nella VLAN 20.

### Configurazione Cisco (Esempio)
*   **Sullo Switch:**
    ```bash
    ! Configura la porta collegata al router come trunk
    interface FastEthernet0/1
     switchport mode trunk
    ```
*   **Sul Router:**
    ```bash
    ! Abilita l'interfaccia fisica
    interface FastEthernet0/0
     no shutdown
    ! Crea la sub-interface per la VLAN 10
    interface FastEthernet0/0.10
     encapsulation dot1Q 10  ! Specifica l'ID della VLAN
     ip address 192.168.10.1 255.255.255.0  ! Assegna l'IP del gateway per la VLAN 10
    ! Crea la sub-interface per la VLAN 20
    interface FastEthernet0/0.20
     encapsulation dot1Q 20
     ip address 192.168.20.1 255.255.255.0  ! Assegna l'IP del gateway per la VLAN 20
    ```

---

## 2. Tecnica con Switch Multilayer (SVI)

*   **Concetto:** Uno **Switch Multilayer** (o Switch di Livello 3) è uno switch avanzato che può eseguire anche funzioni di routing. È la soluzione più moderna e performante.
*   **Come funziona:** Invece di usare un router esterno, il routing tra VLAN avviene **internamente** allo switch. Si creano delle **Interfacce Virtuali dello Switch (SVI - Switched Virtual Interfaces)**.
*   Una SVI è un'interfaccia logica che rappresenta una VLAN e a cui si può assegnare un indirizzo IP. Questo indirizzo IP funge da **gateway predefinito** per tutti i dispositivi in quella VLAN.

### Configurazione Cisco (Esempio)
```bash
! Abilita la funzionalità di routing sullo switch
ip routing

! Crea l'interfaccia virtuale per la VLAN 10 e le assegna un IP
interface Vlan10
 ip address 192.168.10.1 255.255.255.0

! Crea l'interfaccia virtuale per la VLAN 20 e le assegna un IP
interface Vlan20
 ip address 192.168.20.1 255.255.255.0

! Configura le porte fisiche per i dispositivi
interface FastEthernet0/2
 switchport mode access
 switchport access vlan 10

interface FastEthernet0/3
 switchport mode access
 switchport access vlan 20
```
Il routing tra le due VLAN avverrà ora direttamente all'interno dello switch, in modo molto più veloce rispetto alla tecnica "Router on a Stick".
