<img src="https://img.shields.io/badge/Versione-2.5-green"> <img src="https://img.shields.io/badge/Aggiornato-si-orange"> <a href="https://forum.hassiohelp.eu/d/503-package-cronotermostato"><img src="https://img.shields.io/badge/Forum-hassiohelp-blue"></a> <a href="https://www.buymeacoffee.com/mariocandida80"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" width="90" alt="Buy Me A Coffee"></a>  <a href="https://github.com/mariocandida80/Home-Assistant-Cronothermostat">English version</a>
<br>
Per chi vuole la versione settimanale, può integrarla <a href="https://github.com/mariocandida80/addon_settimanale">qui</a>.<br>
Vorrei ringraziare tutto il gruppo <a href="https://www.facebook.com/groups/2062381507393179/">facebook</a> e <a href="https://t.me/HassioHelp">telegram</a> di HassioHelp per il supporto ricevuto. Qui ci sono anche il <a href="https://forum.hassiohelp.eu/">forum</a> e le <a href="https://hassiohelp.eu/">guide</a> molto utili!<br>
Se vi piace il mio lavoro, potete supportarmi su <a href="https://www.paypal.com/paypalme/mariocandida">Paypal</a> oppure <a href="www.buymeacoffee.com/mariocandida80 ">offrimi un caffè</a>.<br>   
<p align="center"/> <b>Package Cronotermostato per Home Assistant.</b> <br> </p>

<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/nuova_principale.png"></p>
Questo package crea una serie di entità ed automazioni per fare in modo che il termostato funzioni in varie
modalità selezionabili dall’utente e che sia possibile accenderlo in determinati orari e se si è o meno in casa. <br>
Vediamo come installarlo. <br>
<br>
<ul>
  <li> <a href="#Prerequisiti">Prerequisiti</a><br></li>
  <li><a href="#Installazione1">Installazione con entità climate non pre installata</a><br></li>
  <li><a href="#Installazione2">Installazione con entità climate già installata</a><br></li>
  <li><a href="#Confcard">Configurazione card</a><br></li>
  <li><a href="#Funzionamento">Funzionamento</a><br></li>
  <li><a href="#Changelog">Change log</a><br></li>
  </ul>

<a name="Prerequisiti"><p align="center"/> <b>Prerequisiti</b> <br> </p>
Per funzionare ha bisogno o di un'entità climate già installata oppure di 2 entità: uno switch che attivi e disattivi il termostato ed un sensore di temperatura. <br>
Per installare questo package avrete bisogno di:<br>
1. aver configurato <a href="https://github.com/mariocandida80/cronotermostato/wiki/Packages-Home-Assistant">i packages</a><br>
2. installare <a href="https://github.com/custom-cards/button-card">button-card</a>, <a href="https://github.com/thomasloven/lovelace-card-mod"> card-mod</a>,  <a href="https://github.com/thomasloven/lovelace-state-switch">state-switch</a> e <a href="https://github.com/pilotak/homeassistant-attributes"> attributes </a> <a href="https://github.com/mariocandida80/cronotermostato/wiki/Installazione-HACS"> (da HACS).</a><br><br>

<a name="Installazione1"><p align="center"/><p align="center"/> <b>Installazione con entità climate non pre installata</b> <br> </p>
Scaricare il file cronotermostato-master.zip (clone or download in alto a destra e poi download zip) e decomprimere i file. <br>
Copiare i file in questo modo:<br>
Pkg_cronotermostato.yaml nella cartella packages <br>
blu.jpg, impostazioni.jpg e fiamma.gif nella cartella www/immagini/lovelace/<br>

Aprire il file Pkg_cronotermostato.yaml ed effettuare le seguenti modifiche:<br>
1. sostituire switch.sonoff_10004b541f con lo switch che accende il termostato (riga 33)<br>
2. sostituire sensor.sonoff_10004b541f_temperature con il sensore della temperatura (riga 34)<br>
3. sostituire device_tracker.iphone7 con il proprio device_tracker (riga 35)<br>
4. sostituire la zona home con la propria zona se è diversa (riga 36<br>
5. sostituire il servizio di notifica con il proprio (riga 37)<br>
6. se si ha già il sensor.time, commentarlo (righe da 156 a 158)<br>
7. se volete un’isteresi, ovvero che il termostato si spenga ad una temperatura superiore o che si riaccenda
ad una inferiore a quella impostata, dovrete modificare hot_tolerance e cold_tolerance.
Esempio: impostando la temperatura a 23 e impostando cold_tolerance a 2 e hot_tollerance a 0, il termostato si spegnerà
quando arriverà a 23 gradi e si riaccenderà a 21. Di default sono impostati cold_tolerance: 0.5 e hot_tolerance: 0.<br>
Riavviare home assistant<br><br>

<a name="Installazione2"><p align="center"/> <b>Installazione con entità climate già installata</b> <br> </p>
Scaricare il file cronotermostato-master.zip (clone or download in alto a destra e poi download zip) e decomprimere i file. <br>
Copiare i file in questo modo:<br>
Pkg_cronotermostato_no_climate.yaml nella cartella packages <br>
blu.jpg, impostazioni.jpg e fiamma.gif nella cartella www/immagini/lovelace/<br>

Aprire il file Pkg_cronotermostato_no_climate.yaml ed effettuare le seguenti modifiche:<br>
1. sostituire device_tracker.dispositivo con il proprio device_tracker (riga 32)<br>
2. sostituire la zona home con la propria zona se è diversa (riga 33)<br>
3. sostituire il servizio di notifica con il proprio (riga 34)<br>
4. sostituire climate.termostato con il proprio (riga 35)<br>
5. se si ha già il sensor.time, commentarlo (righe da 138 a 140)<br>
6. sostituire *termostato con la proprio entità climate (per esempio climate.riscaldameto) alle righe 161 e 168.<br>
Riavviare home assistant<br><br>
<a name="Confcard"><p align="center"/> <b>Per la configurazione della card:</b><br> </p>
Per chi usa la modalità raw, creare una nuova card e copiare il contenuto di lovelace_raw.yaml.<br>
Per chi usa la modalità yaml, aprire il file lovelace_yaml.yaml e copiare il contenuto nel proprio file lovelace.<br>

<a name="Funzionamento"><p align="center"/> <b>Funzionamento</b><br> </p>
<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/nuova_principale.png" alt="Immagine cronotermostato"></p>
Nella card principale vi ritroverete in alto a destra un pulsante per aprire le impostazioni degli orari di accensione e spegnimento per la modalità AUTO e PRERISCALDAMENTO, sotto troverete una fogliolina che apre le impostazioni per la modalità ECO, in alto a sinistra un ingranaggio per aprire le impostazioni, al centro a sinistra c’è la temperatura del vostro sensore mentre a destra la temperatura impostata che potete modificare con le 2 frecce che sono posizionate sopra e sotto; al centro viene indicato da una fiamma se al momento il termostato è acceso o spento; in basso ci sono le 5 modalità di funzionamento; la modalità selezionata sarà evidenziatain giallo.<br>
Ogni giorno alle ore 18:00 e ad ogni riavvio, viene controllato se c'è un aggiornamento che verrà segnalato con un'icona bianca in alto a destra; cliccandoci si aprirà la schermata per aggiornare il package.<br>

<p align="center"/> <b>Modalità di funzionamento</b><br> </p>
Il termostato, è configurato per funzionare in 5 modalità:<br>

OFF: termostato spento.<br>

MANUALE:  termostato acceso, non tiene conto di orari e posizione.<br>

AUTO:  il termostato si accende solo se si è a casa e se l’ora è tra gli intervalli di tempo impostati.<br>

PRE: il termostato si accende all’ora impostata anche se si è fuori casa.<br>

ECO:  imposta una temperatura più bassa, ideale per la notte o se si vuole lasciare una temperatura più bassa quando non
si è a casa.<br><br>

Quando è acceso il termostato, in qualsiasi modalità tranne la OFF, resterà acceso fino a quando non arriverà alla temperatura
impostata e si riaccenderà se la temperatura si riabbasserà. <br>
La modalità ECO si attiva automaticamente all’ora impostata per poi ritornare alla modalità precedente e alla temperatura
precedente una volta che arriva all’ora impostata per lo spegnimento della modalità ECO. È possibile anche attivarla
manualmente cliccando sul bottone ECO. Per disattivarla basta scegliere una modalità diversa e ritornerà anche la
temperatura impostata precedentemente. Volendo disattivare la modalità ECO con gli orari impostati, lo si potrà fare dal menù impostazioni.<br>
<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/nuova_eco.png"> </p>
Dalla pagina iniziale, cliccando sulla fogliolina in alto a destra, si aprirà il menù impostazioni modalità eco.<br>
Qui potete inserire l’orario di accensione e spegnimento della modalità e la temperatura da impostare quando si attiverà
tale modalità.<br>
Cliccando sulla freccia in alto a destra si tornerà alla pagina iniziale.<br><br>
<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/orari.png"> </p>
Dalla pagina iniziale, cliccando sull’icona  in alto a destra, si aprirà il menù impostazioni per l’accensione in
modalita AUTO e PRERISCALDAMENTO.<br>
Qui potrete impostare l’orario di accensione e spegnimento del termostato. Ci sono 3 fasce orarie con possibilità di disabilitare le ultime 2 in caso si voglia far funzionare il termostato con fascia mono-oraria o bi-oraria; basterà cliccare su acceso/spento sopra alla fascia.<br>
Cliccando sulla freccia in alto a destra si tornerà alla pagina iniziale.<br>
<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/nuova_impostazioni.png" alt="nuova impostazioni"></p>
Dalla pagina iniziale, cliccando sull’ingranaggio in alto a sinistra, si aprirà il menù impostazioni del termostato. <br>
Da qui potrete scegliere se attivare o meno la modalità ECO con gli orari impostati.<br>
Potrete selezionare la modalità in uscita ovvero quando siete in modalità AUTO ed uscite di casa; le modalità sono 2: SPEGNIMENTO e ECO. La prima spegne il termostato per riaccenderlo al vostro rientro; la seconda lascia il termostato acceso abbassando la temperatura a quella ECO per poi ripristinare la temperatura precedente al rientro.<br>
L'ultima ozione serve per scegliere se ricevere o meno un messaggio all'accensione del termostato. <br>

<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/aggiornamento.png" alt="aggiornamenti"></p>
Quando compare l'icona aggiornamento sulla pagina principale, cliccandoci sopra si aprirà la pagina degli aggiornamenti. Di volta in volta verrà avvisato se basterà aggiornare solo il package o anche la parte lovelace, ovviamente rispetto alla versione precedente. Da qui basterà cliccare su scarica il package e vi ritroverete la nuova release. Ricordatevi di cambiare le entità nella parte setup. Al termine del download vi darà l'esito proponendo di riavviare cliccando sul pulsante "Riavvia Home Assistant"  in caso di esito positivo oppure di scaricare il package in manuale in caso di esito negativo. Per la parte lovelace, dovrà essere aggiornata manualmente, se dovesse esserci bisogno di aggiornare.<br>
<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/mess%20ok.png" alt="messaggio ok"><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/mess%20not%20ok.png" alt="messaggio not ok"></p>
Per qualsiasi problema scrivete sul <a href="https://forum.hassiohelp.eu/d/503-package-cronotermostato">forum.</a><br>

<a name="Changelog"><p align="center"/> <b>Change log V2.5</b> <br>
Risolto bug per controllo aggiornamenti. Inserita nuova scheda "info" dove è possibile vedere la versione installata e quella più recente.
<a name="Changelog"><p align="center"/> <b>Change log V2.4</b> <br>
Ora è possibile scaricare il package direttamente da lovelace sia per la versione standard e sia per la versione no_climate.
Esito ok o not ok al termine del download con possibilità di riavviare da lovelace dopo il download.</p>
<a name="Changelog"><p align="center"/> <b>Change log V2.3</b> <br>
Aggiunta la possibilità di scaricare il package direttamente da lovelace.</p>
<a name="Changelog"><p align="center"/> <b>Change log V2.2</b> <br>
Risolto problema in cui alcune volte il termostato in modalità auto partiva anche se la fascia oraria era disattivata.</p>
<a name="Changelog"><p align="center"/> <b>Change log V2.0</b> <br>
Aggiunta una notifica quando ci sono nuovi aggiornamenti.
Bug fix.</p>
<a name="Changelog"><p align="center"/> <b>Change log V1.3.6</b> <br>
Risolto bug che quando si cambia una fascia oraria con modalità AUTO già inserita, verifica che sia nella fascia di accensione o spegnimento. </p>
<a name="Changelog"><p align="center"/> <b>Change log V1.3.5</b> <br>
Risolto bug che non faceva accendere il termostato in modalità AUTO con le terza fascia.
Risolto bug che non faceva ritornare nella modalità precedente dalla modalità ECO.</p>
<p align="center"/> <b>Change log V1.3.4</b> <br>
Risolto un bug che faceva passare in modalità OFF quando il termostato è in modalità AUTO alla fine della facia oraria.
Nuova interfaccia grafica. La parte relativa alle impostazioni delle fasce orarie è invariata.
Attenzione che per la nuova interfaccia bisogna aggiungere anche il file impostazioni.jpg nella stessa cartella degli altri 2 file. </p>
<p align="center"/> <b>Change log V1.3.3</b> <br>
Quando si accende o spegne il termostato da app esterna, viene sincronizzato anche su home Assistant impostando Manuale oppure off a seconda del caso.</p>
<p align="center"/> <b>Change log V1.3.2</b> <br>
Aggiunta la possibilità di disattivare l'attivazione della modalità ECO ad orari.<br>
Ora se si cambia la temperatura impostata dal termostato fiscico o da altre app, si sincronizza anche con lovelace.<br>
Risoloto bug in cui al ritorno dalla modalità ECO con orario impostato la temperatura non cambiava.<br>
Per chi ha già installato una versione precedente, sostituite il file fiamma.gif con quello nuovo che ha lo sfondo trasparente.
