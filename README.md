# Tutorial: Wie man Virtuelle Maschinen einrichtet (Eine Anleitung)
v 2.2 | Stand: Dezember 2021 | Lizenz: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.de)

Weitere Anleitungen von uns findet man [hier](https://lehrerlaempel.github.io/anleitungen/)!

# 1 Was hier beschrieben werden soll
Diese Anleitung beschreibt, wie man mit Hilfe von [VirtualBox](https://www.virtualbox.org) Virtuelle Maschinen (VMs) einrichtet und nutzt. Das eigentlich auf dem Computer installierte Betriebssystem wird dabei stets als Host (Gastgeber) bezeichnet. Die einzelnen VMs als Guests (Gäste). In dieser Anleitung wird Windows 10 als Host und LinuxMint als Guest verwendet. Die Anleitung funktioniert aber auch weitestgehend für andere Host/Guest-Konstellationen, da sich die wesentlichen Schritte nicht ändern.

# 2 Wozu Virtuelle Maschinen
Falls Sie sich unter einer VM nichts vorstellen können, finden Sie [hier](https://praxistipps.chip.de/was-ist-eine-virtuelle-maschine-einfach-erklaert_41526) und [hier](https://www.youtube.com/watch?v=yIVXjl4SwVo) kurze gute Erklärungen, was VMs sind.

Die Nutzung von virtuellen Maschinen kann diverse Vorteile haben. Man kann z.B. an einem Computer unkompliziert verschiedene Betriebssysteme parallel nutzen oder ausprobieren. In einer VM kann man auch Systeme und Programme testen und konfigurieren, ohne Schaden am Host zu riskieren. 

Vor allem aber: Sicherheitsempfindliche Tätigkeiten in einer VM bieten den Vorteil, dass im Fall eines Befalls durch Schadsoftware bei guter Handhabung nur die einzelne VM, aber nicht die anderen VMs oder gar der Host befallen werden können. 
Man kann dank Virtualisierung auch installierte Systeme unabhängig von der Hardware machen, da VMs leicht von einem PC auf andere kopiert oder verschoben werden können. So kann zum Beispiel eine VM für die Kommunikation mit Dritten für Abwesenheiten unkompliziert einer Kollegin zur Verfügung gestellt werden, ohne dieser physischen Zugang zum eigenen Laptop gewähren zu müssen.

# 3 Die Grenzen von Virtuellen Maschinen
VMs schützen Sie nur dann, wenn Sie auch tatsächlich Daten und Handeln eines Rechners sinnvoll auf verschiedene VMs aufteilen. Wer also seine Datenhaltung sowie die Kommunikation per Mail etc. komplett in einer VM abwickelt, der gewinnt dadurch im Falle einer Infektion durch Schadsoftware wenig. Sinnvollerweise nutzt man also z.B. für private Onlinerecherche, dienstliche Onlinerecherche, private Messenger und dienstliche Mails jeweils eine eigene VM.

Sämtliche Virtualisierung ist überflüssig, wenn der Host von Schadsoftware befallen ist. Virtualisierung dient also nur dann der Sicherheit, wenn der Host nicht mehr für sicherheitsmepfindiche Tätigkeiten (Surfen, Mailen, etc.) genutzt wird. Im Optimalfall ist der Host also nur die Basis für das Arbeiten in verschiedenen VMs.

# 4 Machen
## 4.1 Systemvoraussetzungen
Um sinnvoll moderne Betriebssysteme zu virtualisieren, benötigen Sie auf dem verwendeten Computer an Arbeitsspeicher/RAM mindestens 4GB plus ungefähr 3GB pro parallel betriebener VM. Zudem benötigen Sie auf Ihrer Festplatte pro VM je nach Nutzung ungefähr 20 bis 40 GB freien Festplattenspeicher. Je schneller dann noch der Prozessor ist, desto weniger Geduld benötigen Sie. Meist sind auf modernen Computern Prozessoren aber nicht das Nadelöhr, sondern eher der (Arbeits-)Speicher.

Vor dem Start sollten Sie in Ihrem BIOS die Virtualisierungsunterstützung aktivieren. Diese trägt meist Bezeichnungen wie "Intel Virtualization Technology" oder so ähnlich. Egal, wie Ihr Hersteller die Option genannt hat und wo er sie in Ihrem BIOS versteckt hat: Suchen Sie die Option und [aktivieren Sie diese](https://www.pctipp.ch/praxis/firmen/programm-verlangt-einschalten-von-virtualisierung-2001928.html).

Wer Windows 10 als Host nutzt, kann mit Strg + Alt + Entf den Task-Manager öffnen. Unter dem Reiter "Leistung" kann dort nachgeschaut werden ob Virtualisierung bereits aktiviert ist uns man sich den Ausflug ins BIOS sparen kann.

## 4.2 Installation VirtualBox
Installieren Sie sich zunächst die für Ihr Betriebssystem passende Version von [VirtualBox](https://www.virtualbox.org/wiki/Downloads).

Laden Sie sich anschließend von der selben Seite das zu der eben installierten Version passende "VirtualBox Extension Pack". Nach einem Doppelklick auf dieses führt Sie Virtualbox durch die Installation. (Das Extension Pack nutzt für alle Betriebssysteme dieselbe Installationsdatei.)

*Selbstverständlich gibt es neben VirtualBox auch noch diverse andere Programme, die VMs betreiben können. Die bekanntesten sind wohl vermutlich [Hyper-V von Microsoft](https://de.wikipedia.org/wiki/Hyper-V), das in vielen Windows-Versionen bereits integriert ist, sowie [VMware Workstation](http://www.vmware.com/de/products/desktop_virtualization/workstation/overview.html). In Linux-Kreisen wird häufig bei dieser Gelegenheit auch [Gnome Boxes](https://apps.gnome.org/de/app/org.gnome.Boxes/) erwähnt. Kann man sicher alle drei nutzen. Wir haben uns hier aber für VirtualBox entschieden, da wir die Bedienung am einfachsten finden, die Software plattformübergreifend funktioniert und sie kostenfrei zur Verfügung steht.*

## 4.3 Zielsystem Downloaden
Laden Sie sich dann ein aktuelles Installationsmedium des Systems herunter, das Sie virtualisieren möchten, zum Beispiel [LinuxMint](https://linuxmint.com/download.php). Meist liegen die Systeme als ISO-Datei (Datenträgerabbild, also quasi virtuelle DVD) vor.

## 4.4 Erstellen der VM
Erstellen Sie nun in VirtualBox durch einen Klick auf *NEU* eine neue VM mit einem aussagekräftigen Namen. Als Typ wählen Sie "Linux", als Version "Ubuntu 64bit". Am besten wählen Sie ungefähr 4.000MB Speicher (RAM) und erstellen eine neue dynamisch allozierte Festplatte mit mindestens 25GB. Wichtig ist beim RAM nur, dass Sie der VM nur so viel Arbeitsspeicher geben, dass am Ende immer noch mindestens 4GB für das Host-Betriebssystem übrig bleiben. 

*Beispie: Sie haben 8GB Arbeitsspeicher. Dann können Sie 743 VMs mit 4 GB Arbeitsspeicher anlegen, aber nie zwei davon gleichzeitg starten, da sonst für Ihren Host nicht genug Arbeitsspeicher übrig bleibt. Lassen Sie dem Host wenn möglich immer 4GB RAm übrig! Vergeben Sie im selben Szenario jedoch nur 2 GB Arbeitsspeicher pro VM, können sie bei 8GB RAM und 2GB pro VM Problemlos zwei VMs parallel starten und es bleibt noch immer genug RAM für den Host übrig.*

*Dynamisch allozierte Festplatte bedeutet, dass auch nur der tatsächlich benötigte Speicherplatz auf Ihrer realen Festplatte verbraucht wird. Es ist also nicht schlimm, wenn die Summer aller theoretischen Festplattengrößen der VMs auf ihrem System den real zur Verfügung stehenden Speicherplatz übersteigt.*

Gehen Sie dann vor dem ersten Start der VM in die Einstellungen der VM (per Rechtsklick in der Übersicht Ihrer VMs). Dort erhöhen Sie unter "System" die Zahl der genutzten CPUs bzw. Prozessoren auf das Maximum und erhöhen dann den Grafikspeicher auf maximum. Erlauben Sie zudem unter "Allgemein" bei "Erweitert" sowohl die Zwischenablage als auch Drag'n'Drop jeweils "bidirektional" (paranoide Nutzer:innen sollten darauf verzichten und mit dem Komforteinbußen leben). Als Grafik-Controller unter "Anzeige" wählen Sie bitte "VBoxSVGA".

Starten Sie die virtuelle Maschine, wählen Sie als Startmedium die heruntergeladene LinuxMint-iso-Datei und installieren Sie in der VM Linux Mint durch einen Klick auf dem Desktop  auf "Install Linux Mint". Lassen Sie auf Nachfrage die ganze Festplatte löschen und Linux Mint installieren. Installieren Sie auch die zusätzlich angebotene proprietäre Software.

Fahren Sie nach der Installation Ihre VM herunter und entfernen Sie über die Einstellungen der VM das eingelegte Installationsmedium, falls Ihnen dieses noch bei den virtuellen Laufwerken angezeigt wird. Starten Sie die VM wieder und klicken Sie nach dem Hochfahren im Fensterrahmen der VM unter Geräte auf Gasterweiterungen einlegen. Nachkurzem Warten können Sie den Installationsprozess durch einen Klick auf "Ausführen" starten. Warten Sie, bis die Installation fertig ist und starten Sie die VM neu.

Spätestens jetzt sollten Sie die Anzeigegröße Ihrer VM bequem durch verändern des Rahmens ändern können. (Falls nicht, klicken Sie oben im Rahmen Ihrer VM durch das Menü, bis sie die Option "Gastanzeige anpassen" gefunden haben.)

Fertig :-)

# 5 Export/Import
Bringen Sie das installierte System zunächst auf den aktuellsten Stand und passen Sie alle Einstellungen nach Ihrem Geschmack an. Versuchen Sie auch, Daten per Drag'n'Drop aus der VM auf das Windows-Desktop und andersrum zu kopieren. Wenn alles wie gewünscht funktioniert und eingerichtet ist, können Sie in VirtualBox über "Datei" -> "Appliance exportieren" auswählen, welche VMs sie exportieren möchten. Sie könne auch mehrere VMs in eine Datei exportieren.

Wählen Sie dann als Format das "Open Virtualization Format 2.0" und den gewünschten Speicherort. Bei Bedarf können Sie die Datei dann noch mit Metadaten versehen und dann exportieren.

Die so erstellte Datei ist ein praktisches BackUp Ihrer Arbeit und kann nun auf jedem anderen PC mit VirtualBox mit per Doppelklick importiert werden. Und das beste: Das geht auch, wenn als Host jeweils andere Betriebssysteme verwendet werden.

# 6 Read Only
In der Startansicht von VirtualBox können Sie sich unter "Datei" -> "Manager für virtuelle Medien" eine Übersicht der vorhandenen Festplatten Ihrer VMs anzeigen lassen. Als "Typ" wird vermutlich bei allen Festplatten "normal" hinterlegt sein. Wenn Sie das jetzt bei einer fertig eingerichteten und ausgeschaltenen VM auf "nicht veränderlich" umstellen, werden zukünftig sämtliche Änderungen nur noch im Arbeitsspeicher hinterlegt, aber nicht mehr auf die Festplatte geschrieben. Sie erhalten also eine Umgebung, die nach jedem Neustart wieder im Urzustand ist. Das kann z.B. für eine Surfumgebung für Recherchezwecke ganz interessant sein.

Wichtig ist nur, dass sie ab und zu den Typ auf "normal" umstellen, dann kurz Updates installieren, bevor Sie wieder zu "nicht veränderlich" wechseln.

# 7 USB-Speicher nutzen
Sobald Sie an ihrem Computer einen USB-Speicher einstecken, wird dieser zunächst im Host angezeigt. Um diesen in der VM nutzen zu können, klicken Sie in der laufenden VM oben unter "Geräte" -> "USB" auf das gewünschte Gerät. Nach einer kurzen Pause steht der USB-Stick dann in der VM zur Verfügung.

Im [Download-Bereich von VirtualBox](https://www.virtualbox.org/wiki/Downloads) finden Sie ein sogenanntes "VirtualBox XXX Oracle VM VirtualBox Extension Pack". Wenn Sie viel mit USB-Sticks arbeiten möchten, installieren Sie vorher das zu Ihrer VirtualBox-Version passende Extension Pack. Danach können Sie in der ausgeschaltenen VM in den Einstellungen unter "USB" den USB 3 Controller auswählen. Das beschleunigt die Nutzung der USB-Speicher erheblich-

# 8 Sonstiges
- Wer das Betriebssystem seiner VM bei der Installation direkt verschlüsselt, muss sich beim Export der VMs oder beim Sichern dieser in BackUps weniger Gedanken machen, wie diese geschützt werden könnten. Auch wer auf einem Computer ohne aktivierte Festplattenverschlüsselung arbeitet, sollte in Erwägung ziehen, seine VMs direkt zu verschlüsseln.
- Sofern Ihr Computer eine SSD-Festplatte hat, sollten Sie unbedingt versuchen, ihre VMs auf dieser zu speichern. Der Geschwindigkeitsunterschied zu VMs auf herkömmlichen Magnetfestplatten ist enorm!
- Per Rechtsklick kann man in der Übersicht von VirtualBox übrigens bequem Desktopverknüpfungen zu einzelnen VMs erstellen.
- Man muss VMs übrigens nicht immer komplett selbst einrichten. Zum Beispiel [hier](https://www.osboxes.org/virtualbox-images/) oder [hier](https://developer.microsoft.com/de-de/windows/downloads/virtual-machines/) gibt es bereits fertige virtuelle Maschinen. Um den Anbietern aber nicht blind vertrauen zu müssen, empfiehlt es sich aber, für persönliche oder sensible Daten verwendete Maschinen immer selbst aufzusetzen.
- Eine spannende Anwendung für VMs ist [Whonix](https://www.whonix.org/#download). Das sind im Endeffekt zwei fertige VMs. Die eine übernimmt das Routing ihres Datenverkehrs durch das TorNetz, die andere können Sie als Workstation nutzen. Spannendes Konzept und ganz bequem mit einem Mausklick importiert!
- Best Practice: Installieren Sie sich zunächst eine VM mit dem Namen "Rohling" und bringen Sie diese auf den neusten Stand. Diese nutzen Sie nicht zum arbeiten, sondern starten diese nur manchmal für Updates. Immer, wenn Sie eine VM benötigen, erstellen Sie einfach via rechter Maustaste auf der Startseite von VirtualBox einen vollständigen Klon, z.B. mit dem Namen "Arbeit: E-Mail", einen weiteren für "Privat: Daten", etc. So müssen Sie nur einmal eine VM einrichten und können dann immer in wenigen Sekunden weitere VMs erstellen.
- Wer langfristig Spaß mit seinen VMs haben will, fährt diese ganz regulär herunter - so wie man es auch mit einem physischen PC machen würde. Ein Klick auf das rote X oben rechts entspricht dem unangekündigten Stecker ziehen beim echten PC. Kann man machen. Geht halt nicht lange gut.

# 9 Das Kleingedruckte
## 9.1 Fehlerteufel
Diese Anleitung wurde von [lehrerlaempel](https://github.com/lehrerlaempel) nach bestem Wissen und Gewissen erstellt. Wir haben die feste Absicht, diese im Laufe der Zeit an Änderungen der erwähnten Software anzupassen und um weitere Aspekte zu ergänzen. Den Stand der Ihnen vorliegenden Version finden Sie ganz am Anfang der Seite.

Ihnen sind Fehler aufgefallen? Sie haben Verbesserungs- oder Änderungswünsche? Dann nehmen Sie gerne [Kontakt](https://lehrerlaempel.github.io/anleitungen/) mit uns auf. Wir sind tatsächlich sehr an Ihrer Rückmeldung interessiert!

Im Rahmen unserer Möglichkeiten haben wir auch versucht sicherzustellen, dass sowohl diese Seite selbst, als auch die von uns verlinkten Seiten sowohl legaler als auch legitimer Natur sind. Sollten uns Fehler unterlaufen sein oder wir änderungen verlinkter Seiten verpasst haben, geben Sie und gerne ein Zeichen, damit wir das zeitnah beheben können.

Wir übernehmen explizit keinerlei Haftung für die hier getroffenen Aussagen oder möglicherweise daraus entstandene Datenverluste oder sonstigen Schäden. Wir haben diese Texte nach bestem Wissen und Gewissen verfasst, sind aber wie alle Menschen fehlbar. Verstehen Sie diese Anleitungen also bitte als aufrichtig wohlmeindende Ratschläge auf Augenhöhe, jedoch ohne jede Gewähr.

## 9.2 Lizenz
Dieser Text steht unter einer CC-Lizenz, ist also quasi schöpferisches Gemeingut.

Sie dürfen:
- **Teilen** das Material in jedwedem Format oder Medium vervielfältigen und weiterverbreiten
- **Bearbeiten** das Material remixen, verändern und darauf aufbauen

Der Lizenzgeber kann diese Freiheiten nicht widerrufen solange Sie sich an die Lizenzbedingungen halten.

Unter folgenden Bedingungen:
- **Namensnennung** Sie müssen angemessene Urheber- und Rechteangaben machen, einen Link zur Lizenz beifügen und angeben, ob Änderungen vorgenommen wurden. Diese Angaben dürfen in jeder angemessenen Art und Weise gemacht werden, allerdings nicht so, dass der Eindruck entsteht, der Lizenzgeber unterstütze gerade Sie oder Ihre Nutzung besonders.
- **Weitergabe unter gleichen Bedingungen** Wenn Sie das Material remixen, verändern oder anderweitig direkt darauf aufbauen, dürfen Sie Ihre Beiträge nur unter derselben Lizenz wie das Original verbreiten. 
- **Keine weiteren Einschränkungen** Sie dürfen keine zusätzlichen Klauseln oder technische Verfahren einsetzen, die anderen rechtlich irgendetwas untersagen, was die Lizenz erlaubt. 

Hinweise:
- Sie müssen sich nicht an diese Lizenz halten hinsichtlich solcher Teile des Materials, die gemeinfrei sind, oder soweit Ihre Nutzungshandlungen durch Ausnahmen und Schranken des Urheberrechts gedeckt sind.
- Es werden keine Garantien gegeben und auch keine Gewähr geleistet. Die Lizenz verschafft Ihnen möglicherweise nicht alle Erlaubnisse, die Sie für die jeweilige Nutzung brauchen. Es können beispielsweise andere Rechte wie Persönlichkeits- und Datenschutzrechte zu beachten sein, die Ihre Nutzung des Materials entsprechend beschränken.

*Dies war eine allgemeinverständliche Zusammenfassung der [Lizenz](https://creativecommons.org/licenses/by-sa/4.0/legalcode.de), die diese nicht ersetzt.*
