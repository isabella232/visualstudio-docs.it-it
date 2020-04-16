---
title: Creare un'installazione offline | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a6a9707d517a8a43d9a9ca156a5f7291ecee9bee
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445064"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Creare un'installazione offline di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio, vedere [Creare un'installazione offline di Visual Studio](/visualstudio/install/create-an-offline-installation-of-visual-studio) o [Creare un'installazione di rete di Visual Studio](/visualstudio/install/create-a-network-installation-of-visual-studio).

Questa pagina descrive come installare Visual Studio 2015 quando non si è connessi a Internet. Tuttavia, per eseguire un'installazione in modalità disconnessa è necessario prima di tutto creare un layout di installazione offline usando un computer connesso a Internet. Ecco come eseguire questa operazione.

> [!IMPORTANT]
> Se il computer offline esegue Windows 7 SP1 o Windows Server 2008 R2, vedere le istruzioni speciali nella sezione [Risolvere i problemi di un'installazione offline](#BKMK_tshoot) di questo argomento.  È necessario seguire queste istruzioni *prima* di installare Visual Studio 2015.

## <a name="installing-by-creating-an-offline-installation"></a><a name="BKMK_Offline"></a> Installazione mediante la creazione di un'installazione offline

#### <a name="to-create-an-offline-installation-layout"></a>Per creare un layout di installazione offline

1. Scegliere l'edizione di Visual Studio che si vuole installare dalla pagina di download [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015).

2. Dopo aver scaricato il programma di installazione in un percorso del file system locale, eseguire "\<nome eseguibile > /layout".

     Ad esempio, eseguire: `vs_enterprise.exe /layout D:\VisualStudio2015`

     Usando l'opzione `/layout` è possibile scaricare quasi tutti i pacchetti di installazione, non solo quelli adatti al computer di download. Questo approccio fornisce i file necessari per eseguire il programma di installazione in qualsiasi posizione e può essere utile per installare componenti non installati in origine.

3. Dopo aver eseguito questo comando verrà visualizzata una finestra di dialogo che consente di modificare la cartella in cui salvare il layout di installazione offline.   Quindi, fare clic sul pulsante **Download.**

     Quando il download del pacchetto ha esito positivo, verrà visualizzato un messaggio che indica **che l'installazione è riuscita! Tutti i componenti specificati sono stati acquisiti correttamente.**

4. Individuare la cartella specificata in precedenza. (Ad esempio, individuare D: VisualStudio2015.) Questa cartella contiene tutto ciò che è necessario copiare in un percorso condiviso o installare un supporto.

    > [!CAUTION]
    > Al momento, Android SDK non supporta un'esperienza di installazione offline. Se si installano gli elementi del programma di installazione di Android SDK in un computer non connesso a internet, l'installazione potrebbe non riuscire. Per altre informazioni, vedere la sezione Risolvere i problemi di un'installazione offline in questo argomento.

5. Eseguire l'installazione dal percorso del file o dal supporto di installazione.

## <a name="updating-an-offline-installation"></a>Aggiornamento di un'installazione offline
 Microsoft ha rilasciato diversi aggiornamenti per Visual Studio 2015. Per aggiornare l'installazione di Visual Studio, è sufficiente scaricare l'edizione desiderata dalla pagina di download [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015). Successivamente, seguire i passaggi descritti in questo argomento per creare un nuovo layout di installazione offline e usarlo per aggiornare la propria copia di Visual Studio 2015.

## <a name="troubleshooting-an-offline-installation"></a><a name="BKMK_tshoot"></a> Risolvere i problemi di un'installazione offline
 Durante l'installazione offline dalla cache di installazione offline potrebbero essere visualizzati messaggi di avviso relativi all'impossibilità di installare alcuni componenti e pacchetti. La tabella seguente include soluzioni possibili per questi scenari.

| Componente o pacchetto | Soluzione |
|-|-|
| Dotfuscator e Analytics Community Edition 5.19.1 (per le edizioni Community, Professional ed Enterprise di Visual Studio installate in **Windows 7 SP1** e **Windows Server 2008 R2**) | Se il computer offline esegue **Windows 7 SP1** oppure **Windows Server 2008 R2**, prima di installare Visual Studio 2015 è necessario eseguire i passaggi seguenti:<br /><br /> 1. Configurare un file o un server Web per scaricare i file CTL.<br /><br /> 2. Reindirizzare l'URL di aggiornamento automatico Microsoft per un ambiente disconnesso.<br /><br /> Per altre informazioni, vedere la pagina [Configure Trusted Roots and Disallowed Certificates](https://technet.microsoft.com/library/dn265983.aspx) (Configurazione di radici attendibili e di certificati non consentiti) sul sito Microsoft TechNet. |
| Installazione di Android SDK (livello API) | Per installare pacchetti Android SDK (livello API) è necessaria una connessione Internet. Se si usa una rete con restrizioni, per installare Visual Studio è necessario consentire l'accesso agli URL seguenti:<br /><br /> -   `https://dl.google.com:443`<br />-   `https://dl-ssl.google.com:443`<br />-   `https://dl-ssl.google.com/android/repository/*`<br /> <br />Per altre informazioni su come risolvere possibili problemi relativi alle impostazioni proxy, vedere il post di blog [Visual Studio 2015 install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (Errori di installazione di Visual Studio 2015 (Android SDK) dietro un proxy). |
| Modelli di elementi di estendibilità di Visual Studio<br /><br /> Estensione GitHub per Visual Studio<br /><br /> PowerShell Tools per Visual Studio | Se non si dispone di una connessione a Internet quando si installa Visual Studio 2015, è possibile usare un feed offline speciale per generare il layout di installazione offline. **Nota:** questo feed speciale include gli aggiornamenti più recenti per Visual Studio 2015. <br /><br /> Per creare il feed offline speciale, eseguire il comando seguente: /layout *Unità:* \VisualStudio2015 /overridefeeduri *URL-per-feed-xml*<br /><br /> Ad esempio, per un feed offline speciale di Visual Studio 2015 Enterprise in lingua inglese, eseguire:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "https://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Per un elenco completo degli URL che è possibile usare per creare un feed offline speciale nella lingua desiderata, vedere la tabella seguente. |

 Usare gli URL seguenti per creare un feed offline speciale specifico della lingua, come descritto nella tabella precedente.

|       Linguaggio        |                            URL                            |
|-----------------------|-----------------------------------------------------------|
| Cinese (semplificato)  | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Cinese (tradizionale) | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Ceco         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Tedesco         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Inglese        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Spagnolo        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Francese         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Italiano        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Giapponese        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Coreano         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Polacco         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portoghese       | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Russo        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Turco        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Vedere anche

- [Installare Visual Studio](install-visual-studio-2015.md)