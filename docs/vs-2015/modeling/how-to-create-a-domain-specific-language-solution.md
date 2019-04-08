---
title: 'Procedura: Creare una soluzione Domain-Specific Language | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3f675b40f250505e654b287fcaa86e70aca4cdd0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969364"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Procedura: Creare una soluzione per un linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un linguaggio specifico di dominio (DSL) viene creato usando un specializzato [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] soluzione.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Prima di iniziare questa procedura, è innanzitutto necessario installare questi componenti:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|SDK di visualizzazione e modellazione di Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-a-domain-specific-language-solution"></a>Creazione di una soluzione Domain-Specific Language  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>Per creare una soluzione domain-specific language  
  
1. Avviare la procedura guidata linguaggio specifico di dominio.  
  
   1. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
   2. Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
   3. Sotto **tipi di progetto**, espandere il **altri tipi di progetto** nodo e fare clic su **estendibilità**.  
  
   4. Fare clic su **finestra di progettazione Domain-Specific Language**.  
  
   5. Nel **nome** , digitare un nome per la soluzione. Fare clic su **OK**.  
  
       Il **Creazione guidata finestra di progettazione di linguaggio specifico di dominio** viene visualizzata.  
  
      > [!NOTE]
      >  Preferibilmente, il nome indipendente dai tipi deve essere un Visual identificatore C# valido, poiché potrebbero essere utilizzata per generare il codice.  
  
      ![Creare finestra di dialogo DSL](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
2. Scegliere un modello DSL.  
  
    Nel **selezionare le opzioni di Domain-Specific Language** pagina, selezionare uno dei modelli di soluzione, ad esempio **linguaggio minimo**. Scegliere un modello simile al linguaggio specifico di dominio che si desidera creare.  
  
    Per altre informazioni sui modelli di soluzione, vedere [scelta di un modello di soluzione Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
3. Immettere un'estensione di file **estensione di File** pagina. Deve essere univoco nel computer in uso e in tutti i computer in cui si desidera installare il linguaggio DSL. Verrà visualizzato il messaggio **Nessuna applicazione o un editor di Visual Studio usano questa estensione**.  
  
   -   Se è stata usata l'estensione in DSL sperimentale precedente che non è stato completamente installato, è comunque possibile cancellarli indietro usando la **reimpostare l'istanza sperimentale** dello strumento, che può trovarsi nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] menu SDK.  
  
   -   Se un'altra [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensione che usa l'estensione di file è stata completamente installata nel computer in uso, è consigliabile disinstallarla. Nel **degli strumenti** menu, fare clic su **gestore estensioni del**.  
  
4. Esaminare e modificare se necessario, i campi nelle pagine rimanenti della procedura guidata. Quando si è soddisfatti con le impostazioni, fare clic su **fine**. Per altre informazioni sulle impostazioni, vedere [pagine della procedura guidata finestra di progettazione DSL](#settings).  
  
    La procedura guidata crea una soluzione che include due progetti, denominati **Dsl** e **DslPackage**.  
  
   > [!NOTE]
   >  Se viene visualizzato un messaggio che avvisa l'utente non di eseguire modelli di testo da origini non attendibili, fare clic su **OK**. È possibile impostare questo messaggio non venga visualizzato anche in questo caso.  
  
##  <a name="settings"></a> Pagine della procedura guidata della finestra di progettazione DSL  
 È possibile lasciare vari campi invariati rispetto ai valori predefiniti. Tuttavia, assicurarsi di che impostare campo dell'estensione di File.  
  
### <a name="solution-settings-page"></a>Pagina delle impostazioni di soluzione  
 **Il modello si desidera basare il linguaggio specifico di dominio?**  
 Scegliere un modello simile al linguaggio specifico di dominio che si desidera creare. I diversi modelli forniscono punti di partenza utili. Quando si seleziona un modello di soluzione, la procedura guidata visualizza una descrizione. Per altre informazioni sui modelli di soluzione, vedere [scelta di un modello di soluzione Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 **Ciò che si desidera assegnare un nome di linguaggio specifico di dominio?**  
 Il valore predefinito è il nome della soluzione. Codice viene generato da questo valore. Deve essere valido come nome di classe C#.  
  
### <a name="file-extension-page"></a>Pagina estensione file  
 **Usare i file di modello quale estensione?**  
 Digitare una nuova estensione di file.  
  
 Verificare che l'estensione di file non è già stata registrata per l'uso in questo computer, come indicato di seguito:  
  
 Cercare nella casella **altri strumenti e applicazioni registrate per gestire questa estensione**. Se viene visualizzato il messaggio **Nessuna applicazione o un editor di Visual Studio usano questa estensione**, è possibile usare questa estensione di file.  
  
 Se viene visualizzato un elenco di strumenti o pacchetti, è necessario eseguire una delle operazioni seguenti:  
  
-   Digitare un'estensione di file diverso.  
  
     \- oppure -  
  
-   Reimpostare il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] istanza sperimentale. Questo verrà annullata la registrazione di tutti i linguaggi specifici di dominio che si sono già compilate. Nel **avviare** menu, fare clic su **tutti i programmi**, **Microsoft Visual Studio 2010 SDK**, **strumenti**e quindi **reimpostare il Istanza di Microsoft Visual Studio 2010 sperimentale**. È possibile ricompilare tutti gli altri linguaggi specifici di dominio che si desidera usare nuovamente.  
  
     \- oppure -  
  
-   Se un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensione che usa l'estensione di file è stata completamente installata nel computer, disinstallarlo. Nel **degli strumenti** menu, fare clic su **gestore estensioni del**.  
  
### <a name="product-settings-page"></a>Pagina delle impostazioni di prodotto  
 **Che cos'è il nome del prodotto a cui appartiene il nuovo linguaggio specifico di dominio?**  
 Il valore predefinito è il nome del linguaggio DSL.  
  
 Questo valore viene utilizzato in Windows Explorer (o Esplora File) per descrivere i file con questa estensione di file.  
  
 **Che cos'è il nome della società a cui appartiene il prodotto?**  
 Il nome della società.  
  
 Questo valore è incorporato nelle proprietà del AssemblyInfo del pacchetto DSL.  
  
 **Che cos'è lo spazio dei nomi radice per i progetti in questa soluzione?**  
 Il valore predefinito è un nome composto dall'azienda e i nomi di prodotto.  
  
### <a name="signing-page"></a>Pagina firma  
 **Creare un file chiave con nome sicuro**  
 L'opzione predefinita consiste nel creare una nuova chiave per firmare l'assembly DSL.  
  
 **Usa chiave esistente con nome sicuro**  
 Usare questa opzione se si desidera integrare il linguaggio DSL con un altro assembly.  
  
 Per altre informazioni sul nome sicuro, vedere [creazione e assembly con nome sicuro](http://go.microsoft.com/fwlink/?LinkId=186073).  
  
## <a name="see-also"></a>Vedere anche  
 [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Glossario di Strumenti Domain-Specific Language](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
