---
title: Creare un'installazione offline di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 0f73247c02034d32a5843c69477f3fdcbdea4410
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949630"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Creare un'installazione offline di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio 2017, vedere [installare Visual Studio 2017 in ambienti di rete non affidabile o larghezza di banda ridotta](https://docs.microsoft.com/visualstudio/install/install-vs-inconsistent-quality-network), o [creazione di un'installazione di rete di Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio) e [Considerazioni speciali per l'installazione di Visual Studio 2017 in un ambiente offline](https://docs.microsoft.com/visualstudio/install/install-visual-studio-in-offline-environment).

Questa pagina descrive come installare Visual Studio 2015 quando non si è connessi a Internet. Tuttavia, per eseguire un'installazione "disconnected", è necessario creare innanzitutto un layout di installazione offline usando un computer connesso a Internet. Ecco come eseguire questa operazione.  

> [!IMPORTANT]
>  Se il computer offline è in esecuzione Windows 7 SP1 o Windows Server 2008 R2, vedere le istruzioni speciali nel [risoluzione dei problemi di un'installazione offline](#BKMK_tshoot) sezione di questo argomento.  È necessario seguire queste istruzioni *prima di* si installa Visual Studio 2015.  

##  <a name="BKMK_Offline"></a> Installazione mediante la creazione di un'installazione offline  

#### <a name="to-create-an-offline-installation-layout"></a>Per creare un layout di installazione offline  

1.  Scegliere l'edizione di Visual Studio che si desidera installare dal [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) pagina di download.  

2.  Dopo aver scaricato il programma di installazione in un percorso del file System, eseguire "\<nome eseguibile > /layout".  

     Ad esempio, eseguire: `vs_enterprise.exe /layout D:\VisualStudio2015`  

     Tramite il `/layout` switch, è possibile scaricare quasi tutti i pacchetti di installazione, non solo quelli adatti al computer di download. Questo approccio offre i file che è necessario eseguire il programma di installazione in qualsiasi posizione e può essere utile se si desidera installare i componenti installati in origine.  

3.  Dopo aver eseguito questo comando, verrà visualizzata una finestra di dialogo che consente di modificare la cartella in cui si desidera risieda il layout di installazione offline.   Successivamente, fare clic il **scaricare** pulsante.  

     Quando il download del pacchetto ha esito positivo, si dovrebbe vedere un messaggio che segnala **installazione completata. Tutti i componenti specificati sono stati acquisiti correttamente.**  

4.  Individuare la cartella specificata in precedenza. (Ad esempio, individuare D:\VisualStudio2015). Questa cartella contiene tutto il che necessario per copiare in un percorso condiviso o supporti di installazione.  

    > [!CAUTION]
    >  Al momento, Android SDK non supporta un'esperienza di installazione offline. Se si installano gli elementi del programma di installazione di Android SDK in un computer non connesso a internet, l'installazione potrebbe non riuscire. Per altre informazioni, vedere la sezione "Risoluzione dei problemi di un'installazione offline" in questo argomento.  

5.  Eseguire l'installazione dal percorso del file o dal supporto di installazione.  

## <a name="updating-an-offline-installation"></a>Aggiornamento di un'installazione offline  
 Microsoft ha rilasciato alcuni aggiornamenti per Visual Studio 2015. Per aggiornare l'installazione di Visual Studio, è sufficiente scaricare l'edizione desiderata dal [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) pagina di download. Successivamente, seguire i passaggi descritti in questo argomento per creare un nuovo layout di installazione offline e quindi utilizzarla per aggiornare la copia di Visual Studio 2015.  

##  <a name="BKMK_tshoot"></a> Risoluzione dei problemi di un'installazione offline  
 Durante l'installazione offline dalla cache di installazione offline potrebbero essere visualizzati messaggi di avviso relativi all'impossibilità di installare alcuni componenti e pacchetti. La tabella seguente include soluzioni possibili per questi scenari.  


|                                                                                       Componente o pacchetto                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                   Soluzione                                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dotfuscator e Analitica Community Edition 5.19.1 (per le edizioni Community, Professional ed Enterprise di Visual Studio, come installata nel **Windows 7 SP1** e **Windows Server 2008 R2**) |                                                                                                                                       Se nel computer offline viene eseguita **Windows 7 SP1** oppure **Windows Server 2008 R2**, è necessario eseguire i passaggi seguenti prima di installare Visual Studio 2015:<br /><br /> 1.  Configurare un file o web server to download the CTL files.<br /><br /> 2.    Redirect the Microsoft Automatic Update URL per un ambiente disconnesso.<br /><br /> Per altre informazioni, vedere la [configurare radici attendibili e certificati non consentiti](https://technet.microsoft.com/library/dn265983.aspx) pagina sul sito Microsoft TechNet.                                                                                                                                       |
|                                                                                  Installazione di Android SDK (livello API)                                                                                   |                                                                        Per installare pacchetti Android SDK (livello API) è necessaria una connessione Internet. Se si usa una rete con restrizioni, per installare Visual Studio è necessario consentire l'accesso agli URL seguenti:<br /><br /> -   http://dl.google.com:443<br />-   http://dl-ssl.google.com:443<br />-   https://dl-ssl.google.com/android/repository/*<br /> <br />Per altre informazioni su come risolvere possibili problemi con le impostazioni proxy, vedere la [gli errori (programma di installazione di Android SDK) dietro un Proxy di installazione di Visual Studio 2015](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) post di blog.                                                                         |
|                             Modelli di elemento di estensibilità di Visual Studio<br /><br /> Estensione GitHub per Visual Studio<br /><br /> PowerShell Tools per Visual Studio                             | Se non si dispone di una connessione a internet quando si installa Visual Studio 2015, è possibile utilizzare una speciale feed offline per generare il layout di installazione offline. **Nota:** questo feed speciale sono inclusi gli aggiornamenti più recenti di Visual Studio 2015. <br /><br /> Per creare speciali feed offline, eseguire il comando seguente: /layout *unità:* \VisualStudio2015 /overridefeeduri *URL al feed xml.*<br /><br /> Ad esempio, per un lingua inglese speciali feed offline di Visual Studio 2015 Enterprise, eseguire:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "http://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Per un elenco completo degli URL che è possibile usare per creare una speciale feed offline nel linguaggio preferito, vedere la tabella seguente. |

 Usare gli URL seguenti per creare un feed offline speciale del specifiche della lingua, come descritto nella tabella precedente.  


|       Linguaggio        |                            URL                            |
|-----------------------|-----------------------------------------------------------|
| Cinese (semplificato)  | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Cinese (tradizionale) | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Ceco         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Tedesco         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Inglese        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Spagnolo        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Francese         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Italiano        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Giapponese        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Coreano         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Polacco         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portoghese       | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Russo        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Turco        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Vedere anche  
 [Installare Visual Studio]()