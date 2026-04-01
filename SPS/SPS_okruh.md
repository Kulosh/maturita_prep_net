# Maturitní témata z předmětu Správa počítačových sítí pro šk. rok 2025/2026

## [1. Topologie a kabely počítačové sítě](/SPS/questions/Q1.md)

Topologie sítě - druhy, srovnání; kabely sítě – metalické kabely, optická vlákna, základní parametry kabelů, použití v jednotlivých topologiích, konektory, způsoby zapojení kabelů (poznat druhy kabelů a konektorů, zapojení křížené a nekřížené kroucené dvojlinky), pojem strukturovaná kabeláž

## [2. Sdílené a nesdílené přenosové médium v sítích a aktivní prvky sítě](/SPS/questions/Q2.md)

Sdílené a nesdílené přenosové medium, přístupové metody - metoda náhodného přístupu, přístupové metody v bezdrátových sítích, kolize a kolizní doména; broadcast a broadcastová doména; standardy síť hardwaru - Ethernet, kolize v Ethernetu – přístupová metoda, řešení kolizí, možnosti vyloučení kolizí v Ethernetu, omezení kolizní domény v Ethernetu, half-duplex a full-duplex v Ethernetu, standardy ethernetovských sítí, kabely a konektory v ethernetovské síti. Aktivní prvky sítě -  REPEATER, HUB, BRIDGE, SWITCH, ROUTER, GATEWAY, princip jejich funkce, souvislost s ISO-OSI a TCP/IP, možnosti použití, rozdíly v přepínání na druhé a třetí vrstvě, výhody náhrady hubu switchem v sítích Ethernet; segmentace sítě – omezení kolizní domény

## 3. Vrstevnaté modely a architektury

Vrstevnaté modely a architektury, model ISO/OSI a architektura TCP/IP - funkce jednotlivých vrstev; paket a struktura paketu, hlavička IP paketu, rámec, segment;  pojem protokol a port, protokoly soustavy TCP/IP, význam jednotlivých protokolů na jednotlivých vrstvách, čísla portů.

## [4. Přenos dat](/SPS/questions/Q4.md)

Přenos dat - paralelní a seriový, asynchronní a synchronní přenos dat, spojovaný a nespojovaný přenos, spojovaná a nespojovaná služba v TCP/IP - realizace, přepínání paketů a okruhů, virtuální spoj, přenos dat v základním  a přeloženém pásmu, modulace, modulační  a přenosová rychlost, šířka pásma, multiplex.

## [5. Adresace v sítích architektury TCP/IP ](/SPS/questions/Q5.md)

IP adresa - třídy IP adres, struktura IP adresy - adresa sítě a uzlu, adresa broadacstu, maska sítě, způsoby zápisu masky, variabilní a konstantní maska, dělení IP sítě na podsítě, výpočet podsítí, zjištění informací o síťovém prostředí v systému Windows a Linux; konfigurace síťového prostředí v systému Windows a Linux;

## [6. Základní pojmy Active Directory](/SPS/questions/Q6.md)

Active Directory, její logická a fyzická struktura, doména, doménový řadič, členský server, doménový strom, doménový les (struktura), vztahy mezi doménami (jednocestné, dvoucestné, tranzitivní), instalace a odinstalace Active Directory, režimy provozu domény – rozdíly, význam; USN, náhrobek, schéma Active Directory, globální katalog – vysvětlení pojmů.

## [7. Fyzická struktura Active Directory](/SPS/questions/Q7.md)

Vysvětlení pojmů fyzická struktura Active Directory, objekt lokality, replikace, druhy replikací, replikace intrasite a intersite – rozdíly, možnosti ovlivnění času replikace mezi řadiči A.D. v různých lokalitách, možnosti ovlivnění ověřování přihlašujících se uživatelů na konkrétním řadiči v konkrétní lokalitě, předvedení tvorby lokalit  a konfigurace procesů replikace.

## [8. Tvorba a správa objektů Active Directory](/SPS/questions/Q8.md)

Logická struktura A.D., uzlové a koncové objekty, doména, kontejner a organizační jednotka (útvar) - rozdíly, lokalita (síť), základní koncové objekty (uživatel, skupina, počítač, kontakt, sdílená složka - jejich význam, tvorba a nastavení), delegování přístupových práv v rámci A.D., dědění práv,  efektivní práva; skupiny a typy skupin z hlediska rozsahu v rámci struktury A.D. (místní, globální, univerzální), jejich působnosti a členství (se zabezpečením, distribuční), význam vnořování skupin, základní přednastavené skupiny – jejich význam; tvorba a konfigurace uživatelských účtů – jejich omezení, vlastnosti, přístupová práva (zabezpečení) – upřesňující funkce, související snap-in moduly, domovské adresáře a profily uživatelů; konzola mmc – možnosti využití, služby a jejich konfigurace, příkaz msconfig.

## [9. Zásady skupin v A.D.](/SPS/questions/Q9.md)

Význam zásad skupin, druhy zásad skupin – místní a GPO (rozdíly); objekty, na kterých lze nastavovat zásady skupin (doména, OU, lokalita) – jejich význam, pravidla pro vytváření GPO; objekty, na které se vztahují nastavené zásady GPO ( uživatel, počítač ) - jejich konfigurace, vztah mezi jednotlivými typy GPO, význam dědění zásad, konfigurace zásad hesel a omezení uživatelských účtů, zásady zabezpečení, zásady aplikací, HW i SW, zásady profilů, šablony pro správu; příkaz gpupdate.

## 10. Práva v Active Directory a v souborovém systému NTFS

Delegování přístupových práv v rámci A.D., význam jednotlivých práv, dědění práv, efektivní práva, konfigurace práv v A.D., NTFS - přístupová práva k souborovému systému, význam jednotlivých práv,  možnosti získání práv k souborovému systému (uživ. účet, skupina, uzlový objekt, dědění, potlačení dědičnosti, efektivní práva), delegování práv k souborovému systému, práva k domovskému adresáři uživatele, sdílená složka a práva ke sdílené složce; vytvoření a konfigurace domovského adresáře uživatelům v Active Directory.

## [11. Směrování](/SPS/questions/Q11.md)

Směrování - účel, druhy směrování (statické dynamické, adaptivní, neadaptivní, distribuované, centralizované, izolované) - vysvětlit, základní algoritmy (link-state, vector-distance, hierarchické) a protokoly (RIP),konfigurace statického a dynamického směrování v systému Windows a Linux; směrovací tabulka – příkazy pro zobrazení a konfigurace směrovací tabulky v systému Windows a Linux; význam položek ve směrovací tabulce,

## [12. Služba DNS v systému Windows Server](/SPS/questions/Q12.md)

Systém symbolických jmen v IP síti – možné způsoby  realizace, doménový systém – důvody realizace, princip funkce, DNS v Internetu – struktura domén, vyhledávání uzlu dle jména v DNS; doména, subdoména, zóna – vysvětlit pojmy, DNS servery – druhy (autoritativní, neautoritativní, primární, sekundární, cahing-only, forwarding-only), funkce v systému DNS, reverzní doména (zóna), kanonický název uzlu, alias uzlu – vysvětlit pojmy, základní záznamy v databázi DNS (A, CNAME, NS, SOA, PTR), vysvětlit druhy záznamů; příkaz nslookup. Konfigurace DNS serveru a DNS klienta v prostředí MS Windows s A.D. i bez. A.D..

## 13. Služba DHCP v systému Windows Server

Dynamické přidělování IP adres – výhody, nevýhody, rozdíl mezi statickým a dynamickým přidělováním IP adres, základní části DHCP služby  ( DHCP klient, DHCP server, DHCP relay) a jejich konfigurace v prostředí Microsoft Windows s A.D. i bez. A.D..; propojení služeb DNS a DHCP v prostředí Microsoft Windows.

## 14. Služby IIS

IIS – význam a možnosti konfigurace jednotlivých služeb IIS; zabezpečení přenosu pomocí SSL certifikátu, vytvoření SSL certifikátu (podepsaný sám sebou); možné způsoby ověření uživatelů služeb IIS (pomocí uživatelských účtů ve Windows bez Active Directory, s Active Directory, ověřování pomocí klientských certifikátů).

## 15. Uživatelské profily

Uživatelské profily, jednotlivé typy a jejich význam – místí, cestovní (roamingový), povinný (mandatorní), význam souboru NTUSER.DAT, adresáře Documents and Settings a domovské adresáře – rozdíl, využití a konfigurace, systémové proměnné %username% a %systemroot% - adresáře All Users a Default User - význam, možnosti konfigurace jednotlivých uživatelských profilů – omezení, kopírování, nastavování a využití víceuživatelského profilu; vytvoření a konfigurace uživatelského profilu a mandatorního profilu v prostředí Active Directory (včetně nastavení práv ke sdíleným složkám profilů)

## 16. Diskový systém pod operačním systémem Windows Server

Základní a dynamické disky, typy svazků dynamických disků – rozdíly a význam, signatura disku, utility pro práci s disky, správce disků – převedení na dynamické disky, konfigurace, souborový systém NTFS,  princip ukládání dat ( metasoubory, atributy ), omezení místa na svazku uživatelům (kvóty) – konfigurace, protokolování a audit kvót.

## 17. Zabezpečení dat

Certifikační server, certifikační autorita, certifikáty, šifrování, druhy šifrování, symetrické a asymetrické šifrování, privátní a veřejný klíč, digitální a elektronický podpis; bezpečnostní cíle šifrování dat ( zabezpečení při přenosu dat, neodmítnutelnost odpovědnosti, zajištění integrity dat ), hash funkce a hash hodnota, časová razítka, instalace a konfigurace certifikační autority v prostředí Windows. Vystavení certifikátů  CA v prostředí Windows pro službu IIS. Vystavení osobních certifikátů uživatelů CA v prostředí Windows.

## [18. Procesy a spouštění programů v systému Linux](/SPS/questions/Q18.md)

Spouštění programů na popředí a na pozadí; pojem proces, ukončení a pozastavení procesu na popředí a na pozadí (fg, bg, & , sekvenční a konkurenční spouštění úloh, rodičovský proces a potomek, skupina procesů a procesy patřící do jedné session,identifikace procesů (číslo úlohy, PID, PPID, PGID, SID), zabíjení procesů (kill ) a signály ( TERM, KILL, STOP, CONT, HUP ), informace o procesech (jobs, ps, top), priorita procesů (nice, renice), plánované spouštění úloh (at, cron, anacron - konfigurace, konfigurační soubory); význam souborového systému /proc, spouštění procesů pod jinou identitou (su, sudo).

## 19. Uživatelské účty v systému Linux

Vytvoření a konfigurace uživatelských účtů a skupin (useradd, groupadd, usermod, groupmod, userdel, groupdel, chage, groups, id, last, passwd, users, who, whoami), konfigurační soubory uživatelských účtů (useradd, login.defs, passwd,  shadow, group) a význam jednotlivých položek v těchto souborech.

## [20. ACL a diskové kvóty](/SPS/questions/Q20.md)

Pojem ACL – výhody proti běžnému nastavení práv, nastavení ACL (setfacl, getfacl), konfigurační soubory, defaultní ACL, kopírování, zálohování ACL. Diskové kvóty v Linuxu, kvóty na uživatele, kvóty na skupinu; aktivace kvótování (quotacheck, quotaon, quotaoff ), konfigurace kvót (edquota, setquota, quotastats); konfigurační soubory kvót.

## [21. Diskový systém LINUXu](/SPS/questions/Q21.md)

Fyzický disk, diskové oblasti, pojmy Master Boot Record , Partition Table, Boot Record rozdělení fyzického disku a konfigurace diskových oblastí (fdisk, sfdisk, parted), přehled a srovnání souborových systémů (ext 2,3,4 ), tvorba, konfigurace a správa souborového systému ( mkfs, mount, umount, dumpe2fs, fsck, badblocks, tune2fs, df, debugfs  ...), základní konfigurační soubory (fstab, mtab)

## [22. Diskové pole RAID v systému Linux](/SPS/questions/Q22.md)

Pojem diskové pole, úrovně diskového pole RAID0, RAID1, RAID5 – odlišnosti z hlediska využití, potřebný počet disků pro realizaci jednotlivých úrovní, vytvoření diskového pole (mdadm), uložení konfigurace disk. pole, vytvoření souborového systému či svazků na diskovém poli, rozšíření diskového pole a následné rozšíření svazku a souborového systému (resize2fs).

## 23. Svazky (LVM) v systému Linux

Pojem svazek, pojmy physical volume, volume group, logical volume, výhody proti běžnému logickému disku, vytvoření svazku, rozšíření svazku, odstranění svazku, svazky a disková pole, konfigurace svazku (pvs, pvcreate, pvremove, pvdisplay, lvs, lvcreate, lvremove, lvdisplay, vgs, vgcreate, vgremove, vgdisplay, vgchange, pvextend, lvextend, resize2fs, lvreduce, vgreduce)

## 24. Základy souborového systému v Linuxu

Soubory zařízení, diskové oblasti, tvorba a konfigurace diskových oblastí (fdisk, sfdisk, parted),  základní pojmy souborového systému (inode, superblok, datový blok, adresářový blok, journal); adresáře – struktura a význam jednotlivých adresářů, typy  souborů ( symbolický odkaz, pevný odkaz, blokové zařízení, znakové zařízení, pojmenovaná roura, adresář), atributy souborů (suid, sgid, sticky, vlastník, skupinový vlastník), základní příkazy (man, cd, ls, cat, vi,  ln, mkdir, rmdir, cp, rm, mv, mkfifo, find, grep, tar).

## [25. Základy konfigurace síťové komunikace a služeb v Linuxu](/SPS/questions/Q25.md)

Základní konfigurace síťového rozhraní ( nmcli, ifconfig, ip, route, konfigurační soubory); DNS server (konfigurační soubory DNS serveru, spouštění DNS serveru a klienta, konfigurace primárního, sekundárního, caching  a forwarding DNS serveru, konfigurace poddomény - glue záznamy).

## 26. Základní operace se soubory, přístupová práva a atributy souborů

Přístupová práva a atributy k souboru – vysvětlit, manipulace s právy a atributy (číselné vyjádření, zobrazení práv a atributů, příkazy ls, chmod, chgrp, chown), přesměrování vstupu a výstupu – k čemu slouží, příklady využití, roura a pojmenovaná roura – k čemu slouží, příklady využití; příkazy man, cd, ls, cat, vi,  ln, mkdir, rmdir, cp, rm, mv, mkfifo, find, grep, tar, touch

## 27. Instalace a odinstalace aplikací v systému Linux

Možnosti instalce aplikací (zdrojové kódy, knihovny, kompilace, instalační balíčky), balíčkovací systém dnf (repozitáře - konfigurace, konfigurační soubory práce s dnf), výhody balíčkovacích systémů; rpm balíčky, řešení závislostí, vlastní příkaz rpm. Instalace ze zdrojových kódů – výhody a nevýhody kompilace - srovnání s balíčkovacím systémem. ( ldd, ./configure, make, makeinstall, gcc ).

## [28. Služba DHCP v systému Linux](/SPS/questions/Q28.md)

DHCP služba v systému Linux - instalace a konfigurace DHCP serveru, klienta, dynamické  a statické přidělování IP dle MAC, nastavení ddns; DHCP služba v různých, vzájemně propojených sítích.

## [29. Služba webového serveru Apache v systému Linux](/SPS/questions/Q29.md)

Web server Apache ( globální nastavení, nastavení defaultního serveru a konfigurace virtuálních serverů na https protokolu, virtuální hosting, Open SSL).

## [30. Služba FTP serveru v systému Linux](/SPS/questions/Q30.md)

Instalace a konfigurace síťových služeb ftp, pasivní a aktivní ftp server; anonymní ftp server, osobní ftp servery uživatelů - zabezpečený přístup, zabezpečený přenos pomocí SSL mezi ftp serverem a ftp klientem) a ssh (instalace a konfigurace ssh, ověřování přístupu pomocí hesel či osobních certifikátů uživatelů).