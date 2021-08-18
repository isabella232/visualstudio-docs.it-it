---
title: 'Procedura: creare una soluzione per un linguaggio specifico di dominio'
description: Informazioni su come creare un linguaggio specifico di dominio (DSL) usando una soluzione Visual Studio specifica.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: dddd3df6669ed401c6097ebd5761ed9a2c5e5660
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040242"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Procedura: creare una soluzione per un linguaggio specifico di dominio
Un linguaggio specifico di dominio (DSL) viene creato usando una soluzione Visual Studio specifica.

## <a name="prerequisites"></a>Prerequisiti

Prima di poter avviare questa procedura, installare questi componenti:

- Visual Studio
- Visual Studio SDK (installato come parte del carico di **lavoro Visual Studio sviluppo di estensioni)**
- SDK di modellazione (installato come Visual Studio componente)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>Creazione di una soluzione Domain-Specific language

1. Avviare la procedura guidata DSL creando un nuovo **Finestra di progettazione Domain-Specific Language** progetto.

   > [!NOTE]
   > Preferibilmente, il nome scelto per il progetto deve essere un identificatore Visual C# valido perché potrebbe essere usato per generare codice.

   ::: moniker range="vs-2017"

   ![Finestra di dialogo per la creazione di una soluzione DSL](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. Scegliere un modello DSL.

    Nella pagina **Selezione Domain-Specific opzioni del linguaggio** selezionare uno dei modelli di soluzione, ad esempio Lingua **minima**. Scegliere un modello simile al DSL che si vuole creare.

    Per altre informazioni sui modelli di soluzione, vedere [Scelta di un modello di soluzione Domain-Specific linguaggio.](../modeling/choosing-a-domain-specific-language-solution-template.md)

3. Immettere l'estensione del nome file nella **pagina Estensione** file. Deve essere univoco nel computer e in tutti i computer in cui si vuole installare il DSL. Verrà visualizzato il messaggio Nessuna applicazione o **editor Visual Studio usare questa estensione.**

   - Se è stata usata l'estensione di file nelle DSL sperimentali precedenti che  non sono state completamente installate, è possibile cancellarle usando lo strumento Reimposta istanza sperimentale, disponibile nel menu sdk di Visual Studio.

   - Se un'Visual Studio che usa questa estensione di file è stata completamente installata nel computer, provare a disinstallarla. Scegliere **Gestione** estensioni **dal** menu Strumenti .

4. Esaminare e, se necessario, modificare i campi nelle pagine rimanenti della procedura guidata. Quando si è soddisfatti delle impostazioni, fare clic su **Fine**. Per altre informazioni sulle impostazioni, vedere Finestra di progettazione DSL [Wizard Pages](#settings).

    La procedura guidata crea una soluzione con due progetti, denominati **Dsl** e **DslPackage**.

   > [!NOTE]
   > Se viene visualizzato un messaggio che avvisa di non eseguire modelli di testo da origini non attendibili, fare clic su **OK.** È possibile impostare questo messaggio in modo che non venga visualizzato di nuovo.

## <a name="the-dsl-designer-wizard-pages"></a><a name="settings"></a> Pagine Finestra di progettazione DSL procedura guidata
 È possibile lasciare diversi campi invariati rispetto ai valori predefiniti. Assicurarsi tuttavia di impostare il campo Estensione file.

### <a name="solution-settings-page"></a>Pagina Impostazioni soluzione
 **Su quale modello si vuole basare il linguaggio specifico di dominio?**
Scegliere un modello simile al DSL che si vuole creare. I diversi modelli forniscono utili punti di partenza. Quando si seleziona un modello di soluzione, nella procedura guidata viene visualizzata una descrizione. Per altre informazioni sui modelli di soluzione, vedere [Scelta di un modello di soluzione Domain-Specific linguaggio.](../modeling/choosing-a-domain-specific-language-solution-template.md)

 **Come si vuole assegnare un nome al linguaggio specifico di dominio?**
Il valore predefinito è il nome della soluzione. Il codice viene generato da questo valore. Deve essere valido come nome di classe C#.

### <a name="file-extension-page"></a>Pagina Estensione file
 **Quale estensione usare i file di modello?**
Digitare una nuova estensione di file.

 Verificare che questa estensione di file non sia già stata registrata per l'uso in questo computer, come indicato di seguito:

 Esaminare in **Altri strumenti e applicazioni registrati per gestire questa estensione.** Se viene visualizzato il messaggio Nessuna applicazione o Visual Studio editor usa questa **estensione,** è possibile usare questa estensione di file.

 Se viene visualizzato un elenco di strumenti o pacchetti, eseguire una delle operazioni seguenti:

- Digitare un'estensione di file diversa.

     \- - oppure -

- Reimpostare la Visual Studio sperimentale. Verrà annullata la registrazione di tutte le DSL create in precedenza. Nel menu **Start** fare clic su Tutti i programmi **, Microsoft Visual Studio SDK 2010** **,** Strumenti e quindi reimpostare l'istanza sperimentale **Microsoft Visual Studio 2010**. È possibile ricompilare qualsiasi altra DSL che si vuole usare di nuovo.

     \- - oppure -

- Se un'Visual Studio che usa questa estensione di file è stata completamente installata nel computer, disinstallarla. Scegliere **Gestione** estensioni **dal** menu Strumenti .

### <a name="product-settings-page"></a>Pagina Impostazioni prodotto
 **Qual è il nome del prodotto a cui appartiene la nuova lingua specifica del dominio?**
Il valore predefinito è il nome DSL.

 Questo valore viene usato in Windows Explorer (o Esplora file) per descrivere i file con questa estensione di file.

 **Qual è il nome della società a cui appartiene il prodotto?**
Nome della società.

 Questo valore viene incorporato nelle proprietà AssemblyInfo del pacchetto DSL.

 **Qual è lo spazio dei nomi radice per i progetti in questa soluzione?**
L'impostazione predefinita è un nome composto dai nomi della società e del prodotto.

### <a name="signing-page"></a>Pagina Firma
 **Creare un file di chiave con nome sicuro** L'opzione predefinita è creare una nuova chiave per firmare l'assembly DSL.

 **Usare una chiave con nome sicuro esistente** Usare questa opzione se si vuole integrare il DSL con un altro assembly.

 Per altre informazioni sulla denominazione con nome sicuro, vedere Creazione e [uso di Strong-Named assembly](/dotnet/standard/assembly/create-use-strong-named).

## <a name="see-also"></a>Vedi anche

- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))