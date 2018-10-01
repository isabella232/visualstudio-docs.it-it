---
title: Pagine delle proprietà, JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f1491c904be7cf44d739add233a05ba5f01b5df1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529883"
---
# <a name="property-pages-javascript"></a>Pagine proprietà, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [pagine delle proprietà, JavaScript](https://docs.microsoft.com/visualstudio/ide/reference/property-pages-javascript).  
  
  
L'opzione **Pagine delle proprietà** consente di accedere alle impostazioni del progetto. È possibile usare le pagine visualizzate in **Pagine delle proprietà** per modificare le proprietà del progetto.  
  
 Per accedere alle proprietà del progetto, selezionare un nodo di progetto in **Esplora soluzioni**. Scegliere **Proprietà** dal menu **Progetto**.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
 In **Pagine delle proprietà** vengono visualizzate le pagine e le opzioni seguenti.  
  
## <a name="configuration-and-platform-page"></a>Pagina Configurazione e piattaforma  
 Usare le opzioni seguenti per selezionare la configurazione e la piattaforma da visualizzare o modificare.  
  
 **Configurazione**  
 Specifica le impostazioni di configurazione da visualizzare o modificare. Le impostazioni sono **Debug** (impostazione predefinita), **Release**, **Tutte le configurazioni** o una configurazione definita dall'utente. Per altre informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).  
  
 **Piattaforma**  
 Specifica le impostazioni della piattaforma da visualizzare o modificare. Le impostazioni sono **Qualsiasi CPU** (impostazione predefinita per le app [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]), **x64**, **ARM**, **x86** o una piattaforma definita dall'utente. Per altre informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).  
  
## <a name="general-page"></a>Pagina Generale  
 Usare le opzioni seguenti per impostare le proprietà generali del progetto.  
  
> [!NOTE]
>  Alcune opzioni sono disponibili solo per le app di Windows Store.  
  
 **Percorso output**  
 Specifica il percorso dei file di output per la configurazione del progetto. Il percorso è relativo. Se si immette un percorso assoluto, questo viene salvato nel progetto. Il percorso predefinito è bin\Debug.  
  
 Quando si usano configurazioni di compilazione semplificate, il sistema del progetto determina se compilare una versione di debug o una versione finale. Quando si fa clic su **Debug**, **Avvia debug** (o si preme F5), la compilazione viene salvata nel percorso di debug, indipendentemente dal valore specificato in **Percorso output**. Tuttavia, il comando **Compila soluzione** del menu **Compila** inserisce la compilazione nel percorso specificato. Per abilitare configurazioni di compilazione avanzate, nella barra dei menu scegliere **Strumenti**, **Opzioni**. Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, selezionare **Generale** e quindi deselezionare la casella di controllo **Mostra configurazioni della build avanzate**. In questo modo, è possibile controllare manualmente tutti i valori di configurazione e specificare se compilare una versione di debug o una finale. Per altre informazioni, vedere [NIB: generale, progetti e soluzioni, finestra di dialogo Opzioni](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
 **Lingua predefinita**  
 Specifica la lingua predefinita per il progetto. L'opzione di lingua selezionata in **Orologio, lingua e opzioni internazionali** nel Pannello di controllo specifica la lingua preferita dell'utente. Specificando una lingua predefinita per il progetto, si garantisce che vengano usate le risorse della lingua predefinita specificate se la lingua preferita dell'utente non corrisponde alle risorse della lingua presenti nell'applicazione.  
  
## <a name="debug-page"></a>Pagina Debug  
 Usare le opzioni seguenti per impostare le proprietà per il comportamento di debug nel progetto.  
  
> [!NOTE]
>  Alcune opzioni sono disponibili solo per le app di Windows Store.  
  
 **Debugger da avviare**  
 Specifica l'host predefinito per il debugger.  
  
-   Selezionare **Computer locale** per avviare l'applicazione nel computer host di Visual Studio. Per altre informazioni, vedere [Esecuzione di app nel computer locale](http://go.microsoft.com/fwlink/?LinkId=234912).  
  
-   Selezionare **Simulatore** per avviare l'applicazione nel simulatore. Per altre informazioni, vedere [Esecuzione di app nel simulatore](http://go.microsoft.com/fwlink/?LinkId=234913).  
  
-   Selezionare **Computer remoto** per avviare l'applicazione in un computer remoto. Per altre informazioni sul debug remoto, vedere [Esecuzione di app in un computer remoto](http://go.microsoft.com/fwlink/?LinkId=234914).  
  
 **Avvia applicazione**  
 Specifica se avviare l'applicazione quando si preme F5 o si fa clic su **Debug**, **Avvia debug**. Selezionare **Sì** per avviare l'applicazione, altrimenti selezionare **No**. Se si seleziona **No**, è comunque possibile eseguire il debug dell'applicazione usando un metodo diverso per avviarla.  
  
 **Tipo di debugger**  
 Specifica i tipi di codice di cui eseguire il debug. Selezionare **Solo script** per eseguire il debug del codice JavaScript. Selezionare **Solo gestito** per eseguire il debug del codice gestito da Common Language Runtime. Selezionare **Solo nativo** per eseguire il debug del codice C++. Selezionare **Nativo con script** per eseguire il debug del codice C++ e JavaScript. Selezionare **Misto (gestito e nativo)** per eseguire il debug del codice gestito e C++.  
  
 **Consenti loopback della rete locale**  
 Specifica se l'accesso all'indirizzo di loopback IP è consentito per i test dell'app. Selezionare **Sì** per consentire l'uso dell'indirizzo di loopback se l'app client si trova nello stesso computer in cui viene eseguita l'applicazione server, altrimenti selezionare **No**. Questa proprietà è disponibile solo se la proprietà **Debugger da avviare** è impostata su **Computer remoto**.  
  
 **Nome computer**  
 Specifica il nome del computer remoto per l'hosting del debugger. Questa proprietà è disponibile solo se **Debugger da avviare** è impostata su **Computer remoto**.  
  
 **Richiedi autenticazione**  
 Specifica se il computer remoto richiede l'autenticazione. Questa proprietà è disponibile solo se **Debugger da avviare** è impostata su **Computer remoto**.



