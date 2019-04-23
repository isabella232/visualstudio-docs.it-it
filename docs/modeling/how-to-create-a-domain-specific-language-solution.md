---
title: 'Procedura: Creare una soluzione per un linguaggio specifico di dominio'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b1799ac2e7124f79d10dcc8860a994e2f182ea7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051349"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Procedura: Creare una soluzione per un linguaggio specifico di dominio
Un linguaggio specifico di dominio (DSL) viene creato usando una soluzione di Visual Studio specializzata.

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare questa procedura, è possibile installare questi componenti:

- Visual Studio
- Visual Studio SDK (installato come parte del **sviluppo di estensioni di Visual Studio** carico di lavoro)
- Modeling SDK (installata come componente di Visual Studio)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>Creazione di una soluzione Domain-Specific Language

1. Avviare la procedura guidata DSL creando un nuovo **progettista del linguaggio specifico di dominio** progetto.

   > [!NOTE]
   > Preferibilmente, il nome scelto per il progetto deve essere un oggetto visivo valido C# identificatore perché potrebbe essere utilizzata per generare il codice.

   ::: moniker range="vs-2017"

   ![Finestra di dialogo per la creazione di una soluzione DSL](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. Scegliere un modello DSL.

    Nel **selezionare le opzioni di Domain-Specific Language** pagina, selezionare uno dei modelli di soluzione, ad esempio **linguaggio minimo**. Scegliere un modello simile al linguaggio specifico di dominio che si desidera creare.

    Per altre informazioni sui modelli di soluzione, vedere [scelta di un modello di soluzione Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Immettere un'estensione di file **estensione di File** pagina. Deve essere univoco nel computer in uso e in tutti i computer in cui si desidera installare il linguaggio DSL. Verrà visualizzato il messaggio **Nessuna applicazione o un editor di Visual Studio usano questa estensione**.

   - Se è stata usata l'estensione in DSL sperimentale precedente che non è stato completamente installato, è comunque possibile cancellarli indietro usando la **reimpostare l'istanza sperimentale** strumento, che sono disponibili nel menu di Visual Studio SDK.

   - Se un'altra estensione di Visual Studio che usa l'estensione di file è stato completamente installata nel computer in uso, è consigliabile disinstallarla. Nel **degli strumenti** menu, fare clic su **gestore estensioni del**.

4. Esaminare e modificare se necessario, i campi nelle pagine rimanenti della procedura guidata. Quando si è soddisfatti con le impostazioni, fare clic su **fine**. Per altre informazioni sulle impostazioni, vedere [pagine della procedura guidata finestra di progettazione DSL](#settings).

    La procedura guidata crea una soluzione che include due progetti, denominati **Dsl** e **DslPackage**.

   > [!NOTE]
   >  Se viene visualizzato un messaggio che avvisa l'utente non di eseguire modelli di testo da origini non attendibili, fare clic su **OK**. È possibile impostare questo messaggio non venga visualizzato anche in questo caso.

## <a name="settings"></a> Pagine della procedura guidata della finestra di progettazione DSL
 È possibile lasciare vari campi invariati rispetto ai valori predefiniti. Tuttavia, assicurarsi di che impostare campo dell'estensione di File.

### <a name="solution-settings-page"></a>Pagina delle impostazioni di soluzione
 **Il modello si desidera basare il linguaggio specifico di dominio?**
Scegliere un modello simile al linguaggio specifico di dominio che si desidera creare. I diversi modelli forniscono punti di partenza utili. Quando si seleziona un modello di soluzione, la procedura guidata visualizza una descrizione. Per altre informazioni sui modelli di soluzione, vedere [scelta di un modello di soluzione Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Ciò che si desidera assegnare un nome di linguaggio specifico di dominio?**
Il valore predefinito è il nome della soluzione. Codice viene generato da questo valore. Deve essere valido come nome di classe c#.

### <a name="file-extension-page"></a>Pagina estensione file
 **Usare i file di modello quale estensione?**
Digitare una nuova estensione di file.

 Verificare che l'estensione di file non è già stata registrata per l'uso in questo computer, come indicato di seguito:

 Cercare nella casella **altri strumenti e applicazioni registrate per gestire questa estensione**. Se viene visualizzato il messaggio **Nessuna applicazione o un editor di Visual Studio usano questa estensione**, è possibile usare questa estensione di file.

 Se viene visualizzato un elenco di strumenti o pacchetti, è necessario eseguire una delle operazioni seguenti:

- Digitare un'estensione di file diverso.

     \- oppure -

- Reimpostare l'istanza sperimentale di Visual Studio. Questo verrà annullata la registrazione di tutti i linguaggi specifici di dominio che si sono già compilate. Nel **avviare** menu, fare clic su **tutti i programmi**, **Microsoft Visual Studio 2010 SDK**, **strumenti**e quindi **reimpostare il Istanza di Microsoft Visual Studio 2010 sperimentale**. È possibile ricompilare tutti gli altri linguaggi specifici di dominio che si desidera usare nuovamente.

     \- oppure -

- Se un'estensione di Visual Studio che usa l'estensione di file è stato completamente installata nel computer, disinstallarlo. Nel **degli strumenti** menu, fare clic su **gestore estensioni del**.

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
 **Creare un file chiave con nome sicuro** l'opzione predefinita consiste nel creare una nuova chiave per firmare l'assembly DSL.

 **Usa chiave esistente con nome sicuro** usare questa opzione se si desidera integrare il linguaggio DSL con un altro assembly.

 Per altre informazioni sul nome sicuro, vedere [creazione e assembly con nome sicuro](http://go.microsoft.com/fwlink/?LinkId=186073).

## <a name="see-also"></a>Vedere anche

- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
