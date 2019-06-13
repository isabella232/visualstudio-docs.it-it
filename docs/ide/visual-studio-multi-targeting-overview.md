---
title: Destinazione versioni di .NET Framework
ms.date: 02/06/2018
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: cb7af190ac7fc5d4d5ce547029689f6c902a6e4f
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747636"
---
# <a name="framework-targeting-overview"></a>Framework come destinazione di panoramica

In Visual Studio, è possibile specificare la versione di .NET che si desidera destinare il progetto. Per le app .NET Framework per l'esecuzione in un altro computer, la versione di framework di destinazione dell'applicazione devono essere compatibile con la versione di framework che viene installata nel computer.

Per altre informazioni sui Framework di destinazione, vedere [Framework di destinazione](/dotnet/standard/frameworks).

È anche possibile creare una soluzione contenente progetti destinati a versioni diverse di .NET. Framework come destinazione consente di garantire che l'applicazione usi solo le funzionalità sono disponibile nella versione del framework specificato.

> [!TIP]
> È anche possibile definire la destinazione delle applicazioni per piattaforme diverse. Per altre informazioni, vedere [Multitargeting](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Funzionalità per la definizione di .NET Framework come destinazione

La definizione della destinazione del framework include le seguenti funzionalità:

- Quando si apre un progetto destinato a una versione precedente di framework, Visual Studio può aggiornare il progetto automaticamente o lasciare la destinazione come-è.

- Quando si crea un progetto .NET Framework, è possibile specificare la versione di .NET Framework che si desidera di destinazione.

- È possibile [come destinazione più Framework](/dotnet/standard/frameworks#how-to-specify-target-frameworks) in un singolo progetto.

- È possibile destinare una versione diversa di .NET in ognuno dei diversi progetti nella stessa soluzione.

- È possibile modificare la versione di .NET che un progetto esistente destinazioni.

   Quando si modifica la versione di .NET che viene destinato un progetto, Visual Studio rende necessaria qualsiasi modifica ai riferimenti e i file di configurazione.

Quando si lavora su un progetto destinato a una versione precedente di framework, Visual Studio in modo dinamico cambia l'ambiente di sviluppo, come indicato di seguito:

- Vengono filtrati gli elementi delle finestre di dialogo **Aggiungi nuovo elemento**, **Aggiungi nuovo riferimento** e **Aggiungi riferimento al servizio** per omettere scelte che non sono disponibili nella versione di destinazione.

- Vengono filtrati i controlli personalizzati nella **Casella degli strumenti** per rimuovere quelli che non sono disponibili nella versione di destinazione e per visualizzare solo i controlli più aggiornati quando sono disponibili più controlli.

- Filtra **IntelliSense** per omettere funzionalità del linguaggio che non sono disponibili nella versione di destinazione.

- Filtra proprietà nella **proprietà** finestra per omettere quelle che non sono disponibili nella versione di destinazione.

- Filtra le opzioni di menu per omettere opzioni che non sono disponibili nella versione di destinazione.

- Per le compilazioni, vengono usate la versione e le opzioni del compilatore appropriate per la versione di destinazione.

> [!NOTE]
> - La definizione della destinazione del framework non garantisce che l'applicazione verrà eseguita correttamente. È necessario testare l'applicazione per assicurarsi che venga eseguita la versione di destinazione.
> - È possibile destinare le versioni di framework precedenti a .NET Framework 2.0.

## <a name="select-a-target-framework-version"></a>Selezione una versione di .NET Framework di destinazione

Quando si crea un progetto .NET Framework, è possibile selezionare la versione di .NET Framework di destinazione dopo aver selezionato un modello di progetto. L'elenco di framework disponibili include le versioni di framework installate applicabili al tipo di modello selezionato. Per i modelli di progetto non .NET Framework, ad esempio i modelli di .NET Core, il **Framework** non viene visualizzato l'elenco a discesa.

::: moniker range="vs-2017"

![Elenco a discesa dei framework in VS 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Elenco a discesa dei framework in VS 2019](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

In un progetto esistente, è possibile modificare la versione di .NET di destinazione nella finestra di dialogo Proprietà progetto. Per altre informazioni, vedere [Procedura: Destinare una versione di .NET](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolve-system-and-user-assembly-references"></a>Risolvere i riferimenti ad assembly di sistema e utente

Per impostare come destinazione una versione di .NET, è necessario installare innanzitutto i riferimenti all'assembly appropriato. È possibile scaricare developer Pack per versioni diverse di .NET nel [.NET downloads](https://www.microsoft.com/net/download/windows) pagina.

Per i progetti .NET Framework, il **Aggiungi riferimento** nella finestra di dialogo Disabilita gli assembly di sistema non pertinenti alla versione di .NET Framework di destinazione in modo che non possano essere inavvertitamente aggiunti a un progetto. Gli assembly di sistema sono file con estensione *dll* inclusi in una versione di .NET Framework. I riferimenti che appartengono a una versione di framework che è superiore alla versione di destinazione non verranno risolto e non è possibile aggiungere controlli che dipendono da tale riferimento. Se si vuole abilitare questo riferimento, reimpostare la destinazione di .NET Framework del progetto su una che include il riferimento. Per altre informazioni, vedere [Procedura: Una versione del framework di destinazione](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Per altre informazioni sui riferimenti ad assembly, vedere [Risoluzione di assembly in fase di progettazione](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Abilitare LINQ

Quando si usa .NET Framework 3.5 o versioni successive, vengono aggiunti automaticamente un riferimento a **System.Core** e un'importazione a livello di progetto per <xref:System.Linq> (solo in Visual Basic). Per usare le funzionalità LINQ, è necessario attivare anche `Option Infer` (solo in Visual Basic). Se si passa a una versione precedente di .NET Framework, il riferimento e l'importazione vengono rimossi automaticamente. Per altre informazioni, vedere [Uso di LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Vedere anche

- [Framework di destinazione](/dotnet/standard/frameworks)
- [Multitargeting (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)