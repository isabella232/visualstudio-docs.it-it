---
title: Microsoft Language Interface Pack (LIP) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text [Visual Studio], multiple languages
- Multilingual User Interface [Visual Studio]
- language switching [Visual Studio]
- MUI [Visual Studio]
- multiple language support [Visual Studio SDK]
- Windows Multilingual User Interface
- UI text language [Visual Studio]
- languages, multiple language support
ms.assetid: dc86304b-65b7-47e6-9314-1dfd02ecfa65
caps.latest.revision: 28
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 647935dce06d74b29271af130686a10fb8cfc1e9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065038"
---
# <a name="microsoft-language-interface-packs-lips-and-visual-studio"></a>Microsoft Language Interface Pack (LIP) e Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con un Windows Language Interface Pack (LIP) è possibile installare una versione localizzata di Windows e quindi installare diversi Language Pack dell'interfaccia utente. I Language Pack dell'interfaccia utente forniscono un'interfaccia utente (UI) localizzata per il sistema operativo. Ad esempio, è possibile installare un Language Interface Pack in giapponese su una versione inglese di Windows e quindi passare dall'interfaccia utente Windows in inglese a quella in giapponese e viceversa. Con i LIP è possibile avere più versioni localizzate di Windows in un unico computer.

 Nei computer in cui sono installati i LIP e più versioni localizzate di Visual Studio, la modifica delle impostazioni della lingua di visualizzazione di Windows influisce sia su Windows che su Visual Studio, quando sono installati i Language Pack corrispondenti.

## <a name="limitations-of-multi-language-installations"></a>Limitazioni delle installazioni multilingue
 Quando si installano diverse versioni localizzate di Visual Studio nello stesso computer, è possibile passare da una lingua all'altra solo tra edizioni corrispondenti. Se ad esempio sono installate una Express Edition in lingua inglese, una Express Edition in lingua tedesca e una Professional Edition, è possibile passare da una lingua all'altra solo con le Express Edition, non con la Professional Edition.

 Visual Studio usa un Language Pack unificato. Per installare più versioni localizzate di questi prodotti, è necessario prima di tutto installare un prodotto localizzato completo e quindi installare uno o più Language Pack.

> [!NOTE]
>  Visual Studio non supporta l'installazione di più versioni localizzate del prodotto localizzato completo nello stesso computer. Dopo avere installato un prodotto localizzato completo, è necessario aggiungere le versioni localizzate mediante i Language Pack. È comunque possibile installare più prodotti localizzati completi delle edizioni Express nello stesso computer.

### <a name="support-for-code-pages"></a>Supporto delle tabelle codici
 Alcuni strumenti di Visual Studio non visualizzano il testo correttamente quando questo contiene caratteri non presenti nella tabella codici corrente. Al posto del testo vengono visualizzati dei punti interrogativi oppure il testo appare danneggiato. Di seguito sono elencati gli strumenti o le aree interessati da questo problema:

-   Siti distribuiti tramite FTP.

-   Nomi di computer non ASCII in alcuni controlli.

-   Strumenti della riga di comando eseguiti all'esterno di Visual Studio.

-   Migrazione guidata di Visual Basic.

-   ActiveX Control Test Container.

-   Visualizzatore oggetti OLE/COM.

-   Strumento di debug Web ISAPI.

-   Progetti di applicazioni MFC con contenuto della Guida HTML.

-   Le interfacce utente di Visual SourceSafe/SCCI vengono reimpostate in lingua inglese quando la tabella dei codici non è compatibile.

-   Visual SourceSafe non supporta i nomi file in formato Unicode.

-   I caratteri definiti dall'utente finale (area di uso privata) non possono essere usati come token o identificatori.

-   I caratteri in latino esteso B non possono essere visualizzati in alcune finestre degli strumenti di Visual Studio quando la tabella codici di Windows è impostata su una lingua dell'Asia orientale.

-   Le sequenze di testo costituite da caratteri provenienti da script in più lingue possono visualizzare il glifo predefinito per alcuni caratteri.

-   L'operazione di copia e incolla di stringhe di script complesse in controlli comuni potrebbe causare la perdita della forma dei caratteri. Usare invece la tastiera nella lingua corrispondente per immettere il testo.

##### <a name="to-correctly-display-characters-that-are-not-included-in-the-current-code-page"></a>Per visualizzare correttamente i caratteri non inclusi nella tabella codici corrente

1.  Fare clic su**Start**, **Pannello di controllo**, quindi aprire **Opzioni internazionali e della lingua** (o **Area geografica** in [!INCLUDE[win8](../includes/win8-md.md)]).

    > [!NOTE]
    >  Per eseguire questa procedura è necessario essere un amministratore del computer.

2.  Fare clic sulla scheda **Avanzate**.

3.  Nell'elenco **Selezionare una lingua per i programmi non Unicode da usare** selezionare la lingua attualmente in uso.

4.  Fare clic su **OK**.

## <a name="changing-the-language-used-for-the-ui-text-in-visual-studio"></a>Modifica della lingua usata per il testo dell'interfaccia utente in Visual Studio
 Quando si installano più versioni localizzate di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nello stesso computer, per l'interfaccia utente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] viene usata l'impostazione predefinita **Come Microsoft Windows**. Questa impostazione indica che [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] visualizzerà il testo dell'interfaccia utente nella lingua specificata come lingua di visualizzazione per il sistema operativo.

> [!NOTE]
>  Se Visual Studio è impostato per usare l'opzione **Come Microsoft Windows** ma non è installato il Language Pack di Visual Studio corrispondente, Visual Studio userà la lingua della prima installazione di Visual Studio.

#### <a name="to-set-the-language-that-is-used-for-the-ui-text-in-visual-studio"></a>Per impostare la lingua usata per il testo dell'interfaccia utente in Visual Studio

1. Scegliere **Opzioni** dal menu **Strumenti**.

2. Nella finestra di dialogo **Opzioni** espandere **Ambiente**, quindi fare clic su **Impostazioni internazionali**.

3. Nell'elenco **Lingua** scegliere la lingua in cui visualizzare il testo dell'interfaccia utente nell'ambiente di sviluppo.

    Per far corrispondere il testo dell'interfaccia utente dell'IDE all'impostazione della lingua di visualizzazione del sistema operativo, selezionare **Come Microsoft Windows**.

   È anche possibile usare il comando devenv per impostare la lingua usata per l'interfaccia utente. Per altre informazioni, vedere [/LCID (devenv.exe)](../ide/reference/lcid-devenv-exe.md).

## <a name="see-also"></a>Vedere anche
 [Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni](../ide/reference/international-settings-environment-options-dialog-box.md)