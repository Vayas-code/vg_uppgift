# Avancerad Nätverksanalys & Trafikflöde  
 
![Bildbeskrivning på hur ett nätverk fungerar](<Screenshot 2026-09-24 083733.png>)  
*Hur fungerar ett datatrafikflöde likt bilden ova?*  
Likt TCP/IP-modellen kan vi nu dela upp datatrafikflödet likt bilden ovan i 4 olika katergorier. Datan behandlas genom kapsling och får från avsändaren - klienten till målservern.   
- Genom Applikationslagret startar hela denna processen från klienten i labbmiljön. Applikationslagret hanterar protokoll och programdata direkt. När användaren går till en webbplats skapas en bigäran, en DNS förfrågan.   
- Nu tar Transportlagret över och säkerställer korrekt överföring mellan processerna på klienten och servern. Transportlagret lägger med portnummer vilket identifierar vilken specefik applikation/tjänst trafiken tillhör.  
- Internetlagret ansvarar för logisitken kring adressering och routing, detta för att det klienten skickar kommer till rätt målserver. Här används IP-adressen när klientens förfrågan når Gatwayn/routern. Nu tillkommer Nat som hanterar användaren privata IP-adress och gör den till en Publik IP-adress för att det ska gå att lämna det lokala nätverket.   
- Nu är vi framme vid länklagret. Här läggs en hårdvaruadress till - en MAC adress. MAc-adressen används redan i det lokala subnätet där klienten använder sig av ARP för att få reda på routerns mac-Adress. Sedan efter kommer nu Mac-adressen ändras vid varje router genom internet fram till målservern medans våran publika IP-adress blir densamma som NAT gav oss.  
--- 
# Jämnförande OS & behörighetsanalys  
Skillnaden i användarrättigheter med linux och windows är att linux använder sig av ett 3 steg behörighets system: ägare, grupp och övriga. Linuc har även 3 olika behörighetsroller: full access - rwe skriva- w och execute -e   
Wiundows använder sig av flertalet olika behörighetroller och du kan in princip välja och sätta personliga behörigheter på varje användare.   
Linux: smidigt, snabbt och inte komplicerat  
Windows: mer komplicerat och användarspecefik behörighet möjlighet.  

Filsystemsäkerhet. Linux. lätt att hitta och se vem som har behörighet till vilken fil/mapp. lätt att genomsöka. Det finns inte specefika behörighetsroller inlagda för specefika användare. Det är lättare med linux att hålla koll och miinska risken att någon får fel behörighet,  
Windowssystemet filskerhet kan absolut vara säkert i och med att man kan sätta mer specefika behörighetsregelr på användare. Dokc lättare att det blir blandadt/fel i behörighetsutdelningen och om en fil ska ha en viss behörighet blir det krångligare och tar längre tid att åtgärda.   
Linux gör det lätt med arv: om Alice  skriver i gemensama undermappen- där hon ligger som gruppmedlem kmr anvndare i samma grupp att kunna se det hon skriver. 

Windows och arv: kompliserat och krångligt i onödan