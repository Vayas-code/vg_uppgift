# Avancerad Nätverksanalys & Trafikflöde  
 
![Bildbeskrivning på hur ett nätverk fungerar](<Screenshot 2026-09-24 083733.png>)  
*Hur fungerar ett datatrafikflöde likt bilden ova?*  
Likt TCP/IP-modellen kan vi nu dela upp datatrafikflödet likt bilden ovan i 4 olika katergorier. Datan behandlas genom kapsling och får från avsändaren - klienten till målservern.   
1. **Klient-labbmiljön ( Application och Transport)**  
Som vi ser i bilden ovan så startar flödet hos klienten där en begäran/förfrågan skapas. Applikationslagret genererar datan som Transportlagret sedan lägger till en portnummer, detta för att kunna identifiera vilken trafik klientens bigäran tillhör.   

2. **Lokalt subnät (Länklagret)**  
Inann datan lämnar klienten måsten den gå genom det lokala nätverket. Här lägger länklagret på rätt hårdvaruadress (MAC-adress) för att fortsätta på nätverkret router.  

3. **Gateway/Router (Internetlagret)**  
Nu når "paketet" den lokala gateway/routern. Internetlagret tar nu över och forstätter hantera routing och IP-adressering. NAT (Network address Translation) översätter klientens privata IP-adress till en publik IP-adress för att "paketet" ska skciaks vidare utanför det lokala nätverket klienten satt på.  

4. **DNS-uppslagning**   
För att "paketet" ska kunna adresseras till rätt målserver görs en DNS-förfrågan. Detta görs om IP-adressen inte redan är känd hos målservern, då görs det en översättning av domännamnet till en publik IP-adress.  

5. **Internet (Routing mellan nätverk)**  
Den publika IP-adressen som tilldelades av NAT förblir densamma hela vägen. ( Liknande en adress på ett kuver kommer vara densamma) MAC-adressen kommer under trafikens gång att ändras/bytas ut mellan varje router längst vägen.  

6. **Målserver (Dekapsling)**  
Sista stegen är nu när "paketet" når slutdestinationen. Nu packas informationen som klienen skickade upp i omvänd ordning som det skickades på.  



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
*Reflektion av hur man sätter upp användare och grupper i linux och Windows*    
**Linux**   
För att lägga till en ny användare i en grupp skriver man likt nedan `sudo usermod -aG "gruppnamn" "användarens namn"`  
Skriv ur ett analys synpunkt varför detta sättet linux gör är bra och hur dom gör det och vad det innebör. Linux använder sig av Least privliage system så när man lägger till användare så får dom minsta möjliga behörighet från start. Sedan finns det ägare,grupp och överiga som man kna "katigoriera" det gör linux snabbt och enkelt men inte så komplicerat eller djupgådene i alla olika behörighetr.   
 
***Filhantering:***  
Om en användare lägger in en textfil i en grupp kommer alla som har tillgång till den se den. jämnfört med Windows där du kan lägga in en fil men inte säkert du ser den då du kan ha behörighet att komma åt filen men inte se något i den ecemeplvis. 


![Linux](<Screenshot 2026-09-24 132354.png>)    
*Windows*  
Windows har ett säkert sätt att tillåta eller inte en användare att komma åt en fil likt `/deny eller /grant` i sin kod. Det gör det säkert genom att redan i början inte tillåta användren att komma åt filen. Windows har även flertalet olika rättigheter inom filer vilket vi ser i bilderna M och F på slutet innebär olika behörigheter. Nu vill vi inte att bob ska komma åt något alls. Då sätter vi deny och F vilket är Full access. detta betyder i scriptet att Bob har inte tillgång till någon full access överhuvudtaget,- då F är "mest behörigeth" 


![lägger till anävndare i gruooer Windows](<Screenshot 2026-09-24 133948.png>)  
![Ger behörighet till grupper Windows](<Screenshot 2026-09-24 133938.png>)  
