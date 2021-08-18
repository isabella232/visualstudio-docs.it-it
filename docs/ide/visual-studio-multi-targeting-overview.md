---
title: Framework .NET di destinazione
description: Informazioni su come specificare la versione del .NET Framework di destinazione del progetto in modo che l'applicazione possa usare solo le funzionalità disponibili nella versione specificata.
ms.date: 03/31/2020
ms.topic: overview
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 10993948fdfe50853908c19f3ba2dcf08cd22621
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048375"
---
# <a name="framework-targeting-overview"></a>Panoramica sull'impostazione dei framework di destinazione

In Visual Studio è possibile specificare la versione di .NET da impostare come destinazione per il progetto. L'impostazione di framework di destinazione consente di garantire che l'applicazione usi solo le funzionalità disponibili nella versione del framework specificata. Per le app .NET Framework da eseguire in un altro computer, la versione del framework per cui viene sviluppata l'applicazione deve essere compatibile con quella installata nel computer.

Una soluzione di Visual Studio può contenere progetti destinati a versioni diverse di .NET.  Si noti tuttavia che è possibile compilare solo in una singola versione di .NET usando condizionali di riferimento per una singola compilazione o in modo ricorsivo per ogni versione.  Per altre informazioni sui framework di destinazione, vedere [Framework di destinazione](/dotnet/standard/frameworks).

> [!TIP]
> È anche possibile definire la destinazione delle applicazioni per piattaforme diverse. Per altre informazioni, vedere [Multitargeting](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Funzionalità per la definizione di .NET Framework come destinazione

La definizione della destinazione del framework include le seguenti funzionalità:

- Quando si apre un progetto destinato a una versione precedente del framework, Visual Studio può aggiornare automaticamente il progetto o lasciare invariata la versione di destinazione.

- Quando si crea un progetto .NET Framework, è possibile specificare la versione di .NET Framework che si vuole impostare come destinazione.

- È possibile [impostare come destinazione più framework](/dotnet/standard/frameworks#how-to-specify-target-frameworks) all'interno dello stesso progetto.

- È possibile impostare come destinazione una versione diversa di .NET in ognuno dei progetti all'interno della stessa soluzione.

- È possibile modificare la versione di .NET a cui è destinato un progetto esistente.

   Quando si modifica la versione di .NET a cui è destinato un progetto, Visual Studio esegue tutte le modifiche necessarie ai riferimenti e ai file di configurazione.

Quando si lavora a un progetto destinato a una versione precedente del framework, Visual Studio modifica in modo dinamico l'ambiente di sviluppo, come indicato di seguito:

- Vengono filtrati gli elementi delle finestre di dialogo **Aggiungi nuovo elemento**, **Aggiungi nuovo riferimento** e **Aggiungi riferimento al servizio** per omettere scelte che non sono disponibili nella versione di destinazione.

- Vengono filtrati i controlli personalizzati nella **Casella degli strumenti** per rimuovere quelli che non sono disponibili nella versione di destinazione e per visualizzare solo i controlli più aggiornati quando sono disponibili più controlli.

- Vengono applicati i filtri **IntelliSense** per omettere funzionalità del linguaggio che non sono disponibili nella versione di destinazione.

- Vengono filtrate le proprietà nella finestra **Proprietà** per omettere quelle che non sono disponibili nella versione di destinazione.

- Vengono filtrate le opzioni di menu per omettere quelle che non sono disponibili nella versione di destinazione.

- Per le compilazioni, vengono usate la versione e le opzioni del compilatore appropriate per la versione di destinazione.

> [!NOTE]
> - La definizione della destinazione del framework non garantisce che l'applicazione verrà eseguita correttamente. È necessario testare l'applicazione per assicurarsi che venga eseguita la versione di destinazione.
> - Non è possibile impostare come destinazione versioni di framework precedenti a .NET Framework 2.0.

## <a name="select-a-target-framework-version"></a>Selezione una versione di .NET Framework di destinazione

Quando si crea un progetto .NET Framework, è possibile selezionare la versione di .NET Framework di destinazione dopo la selezione di un modello di progetto. L'elenco di framework disponibili include le versioni di framework installate applicabili al tipo di modello selezionato. Per i modelli di progetto che non richiedono .NET Framework, ad esempio i modelli per .NET Core, l'elenco a discesa **Framework** non viene visualizzato.

::: moniker range="vs-2017"

![Elenco a discesa dei framework in VS 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Elenco a discesa dei framework in VS 2019](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="change-the-target-framework"></a>Modificare il framework di destinazione

In un progetto Visual Basic, C# o F# esistente è possibile modificare la versione di .NET di destinazione nella finestra di dialogo delle proprietà del progetto. Per informazioni su come modificare la versione di destinazione per i progetti C++, vedere [Modificare il framework di destinazione e il set di strumenti della piattaforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

1. In **Esplora soluzioni** aprire il menu di scelta rapida del progetto che si vuole modificare e quindi scegliere **Proprietà**.

1. Nella colonna sinistra della finestra **Proprietà** scegliere la scheda **Applicazione**.

   ![Scheda Applicazione delle proprietà del progetto](../ide/media/vs_slnexplorer_properties_applicationtab.png)

   > [!NOTE]
   > Dopo aver creato un'app per la piattaforma UWP, non è possibile cambiare la versione di Windows o .NET impostata come destinazione.

1. Nell'elenco **Framework di destinazione** selezionare la versione appropriata.

1. Nella finestra di dialogo di verifica visualizzata scegliere **Sì**.

   Il progetto verrà scaricato. Una volta caricato nuovamente, il progetto sarà destinato alla versione di .NET appena selezionata.

> [!NOTE]
> Se il codice contiene riferimenti a una versione di .NET diversa da quella impostata come destinazione, è possibile che vengano visualizzati dei messaggi di errore durante la compilazione o l'esecuzione del codice. Per risolvere questi errori, modificare i riferimenti. Vedere [Risolvere i problemi relativi agli errori di impostazione di .NET come destinazione](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

> [!TIP]
> A seconda del framework di destinazione, può essere rappresentato nei modi seguenti nel file di progetto:
>
> - Per un'app .NET Core: `<TargetFramework>netcoreapp2.1</TargetFramework>`
> - Per un'app .NET Standard: `<TargetFramework>netstandard2.0</TargetFramework>`
> - Per un'app .NET Framework: `<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>`

## <a name="resolve-system-and-user-assembly-references"></a>Risolvere i riferimenti ad assembly di sistema e utente

Prima di impostare una versione di .NET come destinazione, è necessario installare i riferimenti ad assembly appropriati. È possibile scaricare Developer Pack per versioni diverse di .NET dalla pagina dei [download di .NET](https://www.microsoft.com/net/download/windows).

Per i progetti .NET Framework, la finestra di dialogo **Aggiungi riferimento** disabilita gli assembly di sistema che non pertinenti alla versione di .NET Framework di destinazione, per evitare che vengano aggiunti inavvertitamente a un progetto. Gli assembly di sistema *.dll* file inclusi in una .NET Framework versione. I riferimenti che appartengono a una versione del framework superiore alla versione di destinazione non verranno risolti e non è possibile aggiungere controlli che dipendono da tale riferimento. Se si vuole abilitare questo riferimento, reimpostare la destinazione di .NET Framework del progetto su una che include il riferimento.

Per altre informazioni sui riferimenti ad assembly, vedere [Risoluzione di assembly in fase di progettazione](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Abilitare LINQ

Quando si usa .NET Framework 3.5 o versioni successive, vengono aggiunti automaticamente un riferimento a **System.Core** e un'importazione a livello di progetto per <xref:System.Linq> (solo in Visual Basic). Per usare le funzionalità LINQ, è necessario attivare anche `Option Infer` (solo in Visual Basic). Se si passa a una versione precedente di .NET Framework, il riferimento e l'importazione vengono rimossi automaticamente. Per altre informazioni, vedere [Uso di LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Vedi anche

- [Framework di destinazione](/dotnet/standard/frameworks)
- [Multitargeting (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
