---
title: 'Procedura: creare una soluzione Domain-Specific Language | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 227838334067d33c8a50c81d3a3c013c6baee356
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533081"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Procedura: creare una soluzione per un linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un linguaggio specifico di dominio (DSL) viene creato usando una soluzione specializzata [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="prerequisites"></a>Prerequisiti
 Prima di iniziare questa procedura, è necessario installare innanzitutto i componenti seguenti:

|Prodotto|Collegamento di download|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[SDK di Visual Studio](../extensibility/visual-studio-sdk.md)|
|SDK di visualizzazione e modellazione di Visual Studio|[Download dell'SDK di modellazione](https://www.microsoft.com/download/details.aspx?id=48148)|

## <a name="creating-a-domain-specific-language-solution"></a>Creazione di una soluzione Domain-Specific Language

#### <a name="to-create-a-domain-specific-language-solution"></a>Per creare una soluzione di linguaggio specifico di dominio

1. Avviare la procedura guidata DSL.

   1. Scegliere **Nuovo** dal menu **File**e quindi fare clic su **Progetto**.

   2. Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

   3. In **Tipi progetto**espandere il nodo **altri tipi di progetto** e fare clic su **estensibilità**.

   4. Fare clic su **finestra di progettazione Domain-Specific Language**.

   5. Nella casella **nome** Digitare un nome per la soluzione. Fare clic su **OK**.

       Verrà visualizzata la **procedura guidata finestra di progettazione Domain-Specific Language** .

      > [!NOTE]
      > Preferibilmente, il nome digitato deve essere un identificatore di Visual C# valido perché potrebbe essere usato per generare codice.

      ![Finestra di dialogo per la creazione di una soluzione DSL](../modeling/media/create-dsldialog.png "Create_DSLDialog")

2. Scegliere un modello DSL.

    Nella pagina **Seleziona opzioni di Domain-Specific Language** selezionare uno dei modelli di soluzione, ad esempio **linguaggio minimo**. Scegliere un modello simile al linguaggio DSL che si vuole creare.

    Per ulteriori informazioni sui modelli di soluzione, vedere [scelta di un modello di soluzione Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Immettere un'estensione per il nome **file nella pagina estensione file** . Deve essere univoco nel computer in uso e in tutti i computer in cui si vuole installare il linguaggio DSL. Verrà visualizzato il messaggio **Nessuna applicazione o editor di Visual Studio utilizzerà questa estensione**.

   - Se è stata usata l'estensione del nome file in DSLs sperimentali precedenti che non sono stati completamente installati, è possibile cancellarli usando lo strumento **Reimposta istanza sperimentale** , disponibile nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] menu SDK.

   - Se un'altra [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensione che usa questa estensione di file è stata completamente installata nel computer, è consigliabile disinstallarla. Scegliere **Gestione estensioni**dal menu **strumenti** .

4. Esaminare e, se necessario, modificare i campi nelle pagine rimanenti della procedura guidata. Una volta soddisfatte le impostazioni, fare clic su **fine**. Per ulteriori informazioni sulle impostazioni, vedere [finestra di progettazione DSL pagine della procedura guidata](#settings).

    La procedura guidata crea una soluzione con due progetti, denominati **DSL** e **DslPackage**.

   > [!NOTE]
   > Se viene visualizzato un messaggio che informa che non è possibile eseguire modelli di testo da origini non attendibili, fare clic su **OK**. È possibile impostare questo messaggio in modo che non venga visualizzato di nuovo.

## <a name="the-dsl-designer-wizard-pages"></a><a name="settings"></a>Pagine della procedura guidata Finestra di progettazione DSL
 È possibile lasciare diversi campi senza modifiche rispetto ai valori predefiniti. Tuttavia, assicurarsi di impostare il campo estensione file.

### <a name="solution-settings-page"></a>Pagina Impostazioni soluzione
 **Specificare il modello su cui si desidera basare la lingua specifica del dominio.**
Scegliere un modello simile al linguaggio DSL che si vuole creare. I diversi modelli forniscono punti di partenza pratici. Quando si seleziona un modello di soluzione, nella procedura guidata viene visualizzata una descrizione. Per ulteriori informazioni sui modelli di soluzione, vedere [scelta di un modello di soluzione Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Specificare il nome del linguaggio specifico di dominio.**
Il valore predefinito è il nome della soluzione. Il codice viene generato da questo valore. Deve essere valido come nome di classe C#.

### <a name="file-extension-page"></a>Pagina estensione file
 **Specificare l'estensione da utilizzare per i file di modello**
Digitare una nuova estensione di file.

 Verificare che l'estensione di file non sia già stata registrata per l'uso nel computer, come indicato di seguito:

 Esaminare **gli altri strumenti e applicazioni registrati per gestire questa estensione**. Se viene visualizzato il messaggio **Nessuna applicazione o editor di Visual Studio usa questa estensione**, è possibile usare questa estensione di file.

 Se viene visualizzato un elenco di strumenti o pacchetti, è necessario eseguire una delle operazioni seguenti:

- Digitare un'estensione di file diversa.

     \- - oppure -

- Reimpostare l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] istanza sperimentale. Verrà annullata la registrazione di tutti i DSLs compilati in precedenza. Dal menu **Start** fare clic su **tutti i programmi**, **Microsoft Visual Studio 2010 SDK**, **strumenti**e quindi **reimpostare l'istanza sperimentale Microsoft Visual Studio 2010**. È possibile ricompilare qualsiasi altra DSLs che si vuole usare di nuovo.

     \- - oppure -

- Se un' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensione che usa questa estensione di file è stata completamente installata nel computer, disinstallarla. Scegliere **Gestione estensioni**dal menu **strumenti** .

### <a name="product-settings-page"></a>Pagina Impostazioni prodotto
 **Qual è il nome del prodotto a cui appartiene il nuovo linguaggio specifico di dominio?**
Il valore predefinito è il nome DSL.

 Questo valore viene usato in Esplora risorse (o Esplora file) per descrivere i file con questa estensione di file.

 **Qual è il nome della società a cui appartiene il prodotto?**
Nome della società.

 Questo valore viene incorporato nelle Proprietà AssemblyInfo del pacchetto DSL.

 **Qual è lo spazio dei nomi radice per i progetti in questa soluzione?**
Il valore predefinito è un nome composto dai nomi della società e del prodotto.

### <a name="signing-page"></a>Pagina firma
 **Creazione di un file di chiave con nome sicuro** L'opzione predefinita consiste nel creare una nuova chiave per firmare l'assembly DSL.

 **Usa chiave con nome sicuro esistente** Usare questa opzione se si vuole integrare il linguaggio DSL con un altro assembly.

 Per ulteriori informazioni sulla denominazione sicura, vedere [creazione e utilizzo di assembly con nome sicuro](/dotnet/standard/assembly/create-use-strong-named).

## <a name="see-also"></a>Vedere anche
 [Come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md) [strumenti Domain-Specific Language Glossario](/previous-versions/bb126564(v=vs.100))
