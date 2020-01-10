---
title: Pagine delle proprietà, JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9fa22a4ed52c3e0a1afdda0105716c0de9b3316
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851817"
---
# <a name="property-pages-javascript"></a>Pagine proprietà, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L'opzione **Pagine delle proprietà** consente di accedere alle impostazioni del progetto. È possibile usare le pagine visualizzate in **Pagine delle proprietà** per modificare le proprietà del progetto.

 Per accedere alle proprietà del progetto, selezionare un nodo di progetto in **Esplora soluzioni**. Scegliere **Proprietà** dal menu **Progetto**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 In **Pagine delle proprietà** vengono visualizzate le pagine e le opzioni seguenti.

## <a name="configuration-and-platform-page"></a>Pagina Configurazione e piattaforma
 Usare le opzioni seguenti per selezionare la configurazione e la piattaforma da visualizzare o modificare.

 **Configurazione** di Specifica le impostazioni di configurazione da visualizzare o modificare. Le impostazioni sono **Debug** (impostazione predefinita), **Release**, **Tutte le configurazioni** o una configurazione definita dall'utente. Per altre informazioni, vedere [Debug and Release Project Configurations](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).

 **Piattaforma** Specifica le impostazioni della piattaforma da visualizzare o modificare. Le impostazioni sono **Qualsiasi CPU** (impostazione predefinita per le app [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]), **x64**, **ARM**, **x86** o una piattaforma definita dall'utente. Per altre informazioni, vedere [Debug and Release Project Configurations](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).

## <a name="general-page"></a>Pagina generale
 Usare le opzioni seguenti per impostare le proprietà generali del progetto.

> [!NOTE]
> Alcune opzioni sono disponibili solo per le app di Windows Store.

 **Percorso di output** Specifica il percorso dei file di output per la configurazione del progetto. Il percorso è relativo. Se si immette un percorso assoluto, questo viene salvato nel progetto. Il percorso predefinito è bin\Debug.

 Quando si usano configurazioni di compilazione semplificate, il sistema del progetto determina se compilare una versione di debug o una versione finale. Quando si fa clic su **Debug**, **Avvia debug** (o si preme F5), la compilazione viene salvata nel percorso di debug, indipendentemente dal valore specificato in **Percorso output**. Tuttavia, il comando **Compila soluzione** del menu **Compila** inserisce la compilazione nel percorso specificato. Per abilitare configurazioni di compilazione avanzate, nella barra dei menu scegliere **Strumenti**, **Opzioni**. Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, selezionare **Generale** e quindi deselezionare la casella di controllo **Mostra configurazioni della build avanzate**. In questo modo, è possibile controllare manualmente tutti i valori di configurazione e specificare se compilare una versione di debug o una finale. Per altre informazioni, vedere [penne: generale, progetti e soluzioni, finestra di dialogo Opzioni](https://msdn.microsoft.com/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).

 **Lingua predefinita** Specifica la lingua predefinita per il progetto. L'opzione di lingua selezionata in **Orologio, lingua e opzioni internazionali** nel Pannello di controllo specifica la lingua preferita dell'utente. Specificando una lingua predefinita per il progetto, si garantisce che vengano usate le risorse della lingua predefinita specificate se la lingua preferita dell'utente non corrisponde alle risorse della lingua presenti nell'applicazione.

## <a name="debug-page"></a>Pagina Debug
 Usare le opzioni seguenti per impostare le proprietà per il comportamento di debug nel progetto.

> [!NOTE]
> Alcune opzioni sono disponibili solo per le app di Windows Store.

 **Debugger da avviare** Specifica l'host predefinito per il debugger.

- Selezionare **Computer locale** per avviare l'applicazione nel computer host di Visual Studio. Per altre informazioni, vedere [Esecuzione di app nel computer locale](https://msdn.microsoft.com/library/windows/apps/hh441483(v=VS.85).aspx).

- Selezionare **Simulatore** per avviare l'applicazione nel simulatore. Per altre informazioni, vedere [Esecuzione di app nel simulatore](https://msdn.microsoft.com/library/windows/apps/hh441475(v=VS.85).aspx).

- Selezionare **Computer remoto** per avviare l'applicazione in un computer remoto. Per altre informazioni sul debug remoto, vedere [Esecuzione di app in un computer remoto](https://msdn.microsoft.com/library/windows/apps/hh441469(v=VS.85).aspx).

  **Avvia applicazione** Specifica se avviare l'applicazione quando si preme F5 o si fa clic su **debug**, **Avvia debug**. Selezionare **Sì** per avviare l'applicazione, altrimenti selezionare **No**. Se si seleziona **No**, è comunque possibile eseguire il debug dell'applicazione usando un metodo diverso per avviarla.

  **Tipo di debugger** Specifica i tipi di codice di cui eseguire il debug. Selezionare **Solo script** per eseguire il debug del codice JavaScript. Selezionare **Solo gestito** per eseguire il debug del codice gestito da Common Language Runtime. Selezionare **Solo nativo** per eseguire il debug del codice C++. Selezionare **Nativo con script** per eseguire il debug del codice C++ e JavaScript. Selezionare **Misto (gestito e nativo)** per eseguire il debug del codice gestito e C++.

  **Consenti loopback della rete locale** Specifica se l'accesso all'indirizzo di loopback IP è consentito per il test dell'app. Selezionare **Sì** per consentire l'uso dell'indirizzo di loopback se l'app client si trova nello stesso computer in cui viene eseguita l'applicazione server, altrimenti selezionare **No**. Questa proprietà è disponibile solo se la proprietà **Debugger da avviare** è impostata su **Computer remoto**.

  **Nome del computer** Specifica il nome del computer remoto in cui ospitare il debugger. Questa proprietà è disponibile solo se **Debugger da avviare** è impostata su **Computer remoto**.

  **Richiedi autenticazione** Specifica se il computer remoto richiede l'autenticazione. Questa proprietà è disponibile solo se **Debugger da avviare** è impostata su **Computer remoto**.
