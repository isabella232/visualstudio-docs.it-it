---
title: Introduzione a servizio di linguaggio e le estensioni dell'Editor | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d2ca0b3a4c1128c316ca2967033752ab45799648
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526986"
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Introduzione alle estensioni dell'editor e dei servizi di linguaggio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Introduzione a servizio di linguaggio e le estensioni dell'Editor](https://docs.microsoft.com/visualstudio/extensibility/getting-started-with-language-service-and-editor-extensions).  
  
È possibile usare le estensioni dell'editor per aggiungere funzionalità del servizio linguaggio, ad esempio la struttura, corrispondenza parentesi graffe, IntelliSense e lampadine per il proprio linguaggio di programmazione o a qualsiasi tipo di contenuto. È anche possibile personalizzare l'aspetto e il comportamento dell'editor di Visual Studio, ad esempio colore, i margini, le aree di controllo e altri elementi visivi come testo. È anche possibile definire il tipo di contenuto e specificare l'aspetto e il comportamento delle visualizzazioni testo in cui viene visualizzato il contenuto.  
  
 Per iniziare a scrivere le estensioni dell'editor, usare i modelli di progetto di editor che vengono installati come parte di Visual Studio SDK. Visual Studio SDK è un insieme scaricabile di strumenti che rendono più semplice sviluppare estensioni di Visual Studio mediante pacchetti VSPackage o mediante Managed Extensibility Framework (MEF).  
  
> [!NOTE]
>  Per altre informazioni su Visual Studio SDK, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
 È consigliabile conoscere i seguenti concetti e tecnologie prima di scrivere le proprie estensioni dell'editor.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Estensioni dell'Editor e Windows Presentation Foundation (WPF)  
 L'interfaccia utente dell'editor di Visual Studio (UI) viene implementato utilizzando Windows Presentation Foundation (WPF). WPF fornisce un'avanzata esperienza visiva e un modello di programmazione coerente che separa gli aspetti visivi del codice dalla logica di business. È possibile usare molti elementi WPF e funzionalità quando si creano estensioni dell'editor. Per altre informazioni, vedere [Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) e le estensioni dell'Editor  
 Editor di Visual Studio Usa Managed Extensibility Framework (MEF) per gestire i suoi componenti e le estensioni. La libreria MEF consente inoltre agli sviluppatori più facilmente creare estensioni per un'applicazione host, ad esempio Visual Studio. In questo framework, si definisce un'estensione in base a un contratto MEF ed esportarlo come parte del componente MEF. L'applicazione host gestisce le parti di componente da trovare, la relativa registrazione e assicurandosi che vengono applicati al contesto corretto.  
  
> [!NOTE]
>  Per altre informazioni su MEF nell'editor, vedere [Managed Extensibility Framework nell'Editor](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Punti di estensione di Editor di Visual Studio ed estensioni  
 Punti di estensione dell'editor sono parti componente MEF che è possibile personalizzare ed estendere. In alcuni casi si estende il punto di estensione che implementa un'interfaccia ed esportandolo con i metadati corretti. In altri casi sufficiente dichiarare un'estensione ed esportarlo come un determinato tipo.  
  
 Di seguito sono riportati alcuni dei tipi di base di estensioni dell'editor:  
  
-   Le barre di scorrimento e i margini  
  
-   Tag  
  
-   Aree di controllo  
  
-   Opzioni  
  
-   IntelliSense  
  
 Per altre informazioni sui punti di estensione di editor, vedere [servizio di linguaggio e punti di estensione Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Distribuzione di estensioni di Editor  
 In Visual Studio, si distribuisce le estensioni dell'editor aggiungendo un file di metadati denominato vsixmanifest alla soluzione, la compilazione della soluzione, e quindi aggiungendo una copia dei file binari e il manifesto in una cartella in cui è noto a Visual Studio. Il file manifesto definisce le informazioni di base relativi all'estensione (ad esempio, nome, autore, versione e tipo di contenuto). Per altre informazioni su come distribuire le estensioni e il file manifesto VSIX, vedere [spedizione di estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Quando si installa un'estensione in un computer, includere i file binari e il manifesto in una sottocartella della cartella in cui è noto a Visual Studio.  
  
> [!WARNING]
>  Non è necessario preoccuparsi dei dettagli dei manifesti e percorsi di distribuzione se si usa uno dei modelli di estendibilità editor inclusi in Visual Studio. I modelli contengono tutto il necessario per registrare e distribuire un'estensione.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Estensioni in esecuzione nell'istanza sperimentale  
 È possibile isolare la versione di lavoro di Visual Studio mentre si sta sviluppando un'estensione distribuendolo in cartella sperimentale seguente (in Windows Vista e Windows 7):  
  
 *% LOCALAPPDATA %* \VisualStudio\10.0Exp\Extensions\\*società*\\*ExtensionID*  
  
 in cui *% LOCALAPPDATA %* è il nome dell'utente connesso *società* è il nome della società che possiede l'estensione, e *ExtensionID* è l'ID dell'estensione.  
  
 Quando si distribuisce un'estensione per il percorso sperimentale, viene eseguito in modalità di debug. Una seconda istanza di Visual Studio viene avviata e viene denominata **Microsoft Visual Studio - istanza sperimentale**.  
  
## <a name="managing-extensions"></a>Gestione delle estensioni  
 Estensioni per Visual Studio sono elencate **estensioni e aggiornamenti** (nelle **strumenti** menu). Se si sta testando un'estensione nell'istanza sperimentale, viene elencata **estensioni e aggiornamenti** nell'istanza sperimentale, ma non è presente nell'istanza di sviluppo.  
  
 Per altre informazioni, vedere [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Usare modelli per creare estensioni dell'Editor  
 È possibile utilizzare editor modelli per creare estensioni MEF che consentono di personalizzare i margini classificatori e le aree di controllo. Sono disponibili modelli per progetti c# e Visual Basic. Per altre informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 È anche possibile usare il modello di progetto VSIX per creare estensioni. Questo modello vengono forniti solo gli elementi necessari per distribuire qualsiasi tipo di estensione e includere il file vsixmanifest, i riferimenti ad assembly richiesti e un file di progetto che include le attività di compilazione che consentono di distribuire la estensione. Per altre informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).  
  
 È anche possibile creare editor di componenti MEF da un'estensione del pacchetto di Visual Studio. Le procedure dettagliate seguenti per informazioni dettagliate, vedere:  
  
-   [Procedura dettagliata: Uso di un comando della shell con un'estensione dell'editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Procedura dettagliata: Uso di una combinazione di tasti con un'estensione dell'editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)

