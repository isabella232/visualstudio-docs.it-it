---
title: Informazioni sulle configurazioni della build
description: Informazioni su come sono necessarie configurazioni di compilazione quando è necessario compilare i progetti con impostazioni diverse in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/20/2020
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ca57bf1e65852e0071f2d84c529309ac46a066fd2a9b629ec16c7f94dd44614b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121232003"
---
# <a name="understand-build-configurations"></a>Informazioni sulle configurazioni della build

Sono necessarie configurazioni di compilazione quando è necessario compilare i progetti con impostazioni diverse. Debug e **Release,** ad **esempio, sono** configurazioni e durante la compilazione vengono usate opzioni del compilatore diverse.  Una configurazione è attiva e viene indicata nella barra dei comandi nella parte superiore dell'IDE.

![Configurazione attiva](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Build configurations in Visual Studio for Mac](/visualstudio/mac/configurations) (Compilazione di configurazioni in Visual Studio for Mac).

La configurazione e il controllo della piattaforma in cui vengono archiviati i file di output compilati. In genere, quando Visual Studio compila il progetto, l'output viene inserito in una sottocartella del progetto denominata con la configurazione attiva (ad esempio, *bin/Debug/x86),* ma è possibile modificare questa impostazione.

È possibile creare configurazioni di compilazione personalizzate a livello di soluzione e di progetto. La configurazione della soluzione determina quali progetti vengono inclusi nella compilazione quando tale configurazione è attiva. Verranno compilati solo i progetti specificati nella configurazione della soluzione attiva. Se vengono selezionate più piattaforme di destinazione Gestione configurazione, vengono compilati tutti i progetti che si applicano a tale piattaforma. La configurazione del progetto determina quali impostazioni di compilazione e opzioni del compilatore vengono usate quando si compila il progetto.

Per creare, selezionare, modificare o eliminare una configurazione, è possibile usare **Gestione configurazione**. Per aprirlo, sulla barra dei menu scegliere Compila Gestione configurazione oppure digitare  >   **Configurazione** nella casella di ricerca. È inoltre possibile usare l'elenco **Configurazioni soluzione** sulla barra degli strumenti **Standard** per selezionare una configurazione o aprire **Gestione configurazione**.

![Configuration Manager](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Se non è possibile trovare le impostazioni di configurazione della soluzione sulla barra degli strumenti e non è possibile accedere al Gestione configurazione **,** è possibile che le impostazioni di sviluppo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] siano applicate. Per altre informazioni, vedere [Procedura: Gestire configurazioni di compilazione applicando le impostazioni di Visual Basic Developer](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Per impostazione predefinita, **le configurazioni** **Debug e Release** sono incluse nei progetti creati tramite [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelli. Una **configurazione** di debug supporta il debug di un'app e una configurazione **release** compila una versione dell'app che può essere distribuita. Per altre informazioni, vedere [Procedura: Impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md). È inoltre possibile creare configurazioni personalizzate per progetti e soluzioni. Per altre informazioni, vedere [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Configurazioni di soluzioni

In una configurazione per la soluzione viene specificato il modo in cui i progetti di una soluzione devono essere compilati e distribuiti. Per modificare una configurazione per la soluzione o per definirne una nuova, in **Gestione configurazione**, sotto la voce **Configurazione soluzione attiva** scegliere **Modifica** o **Nuovo**.

Ogni voce nella casella **Contesti progetto** di una configurazione per la soluzione rappresenta un progetto nella soluzione. Per ogni combinazione di **Configurazione soluzione attiva** e **Piattaforma soluzione attiva**, è possibile definire il modo in cui ogni progetto viene usato. Per altre informazioni sulle piattaforme per la soluzione, vedere [Informazioni sulle piattaforme di compilazione](../ide/understanding-build-platforms.md).

Quando si definisce una nuova configurazione per la soluzione e si seleziona la casella di controllo **Crea nuove configurazioni progetto**, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene assegnata automaticamente la nuova configurazione a tutti i progetti. In modo analogo, quando si definisce una nuova configurazione per la soluzione e si seleziona la casella di controllo **Crea nuove piattaforme progetto**, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene assegnata automaticamente la nuova configurazione a tutti i progetti. Inoltre, se si aggiunge un progetto destinato a una nuova piattaforma, in Visual Studio tale piattaforma viene aggiunta all'elenco delle piattaforme per la soluzione e assegnata a tutti i progetti. È ancora possibile modificare le impostazioni per ogni progetto.

La configurazione per la soluzione attiva fornisce anche il contesto all'IDE. Se, ad esempio, si sta lavorando a un progetto e nella configurazione per la soluzione attiva viene specificata la compilazione per un dispositivo mobile, nella **Casella degli strumenti** verranno visualizzati solo gli elementi del progetto che possono essere usati in un progetto per un dispositivo mobile.

## <a name="project-configurations"></a>Configurazioni di progetto

La configurazione e la piattaforma di destinazione di un progetto vengono usate insieme per specificare le impostazioni di compilazione e le opzioni del compilatore da usare quando viene compilato. Un progetto può avere impostazioni diverse per ogni combinazione di configurazione e piattaforma. Per modificare le proprietà di un progetto, aprire il menu di scelta rapida per il progetto in **Esplora soluzioni**, quindi scegliere **Proprietà**.  Nella parte superiore della scheda **Compilazione di** Creazione progetti scegliere una configurazione attiva per modificarne le impostazioni di compilazione.

![Project della finestra di progettazione](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>Compilazione di più configurazioni

Quando si compila una soluzione usando il **comando** Compila  >  **soluzione,** Visual Studio compila solo la configurazione attiva. Vengono compilati tutti i progetti specificati nella configurazione della soluzione e l'unica configurazione di progetto compilata è quella specificata nella configurazione della soluzione attiva e nella piattaforma della soluzione attiva, visualizzata nella barra degli strumenti di Visual Studio. Ad esempio, **Debug** e **x86**. Altre configurazioni e piattaforme definite non vengono compilate.

Se si vogliono compilare più configurazioni e piattaforme in un'unica azione, è possibile usare **l'opzione Build** Batch  >  Build (Compila compilazione **batch)** in Visual Studio. Per accedere a questa funzionalità, **premere CTRL** + **Q** per aprire la casella di ricerca e immettere `Batch build` . La compilazione batch non è disponibile per tutti i tipi di progetto. Vedere [Procedura: Compilare più configurazioni contemporaneamente.](how-to-build-multiple-configurations-simultaneously.md)

## <a name="how-visual-studio-assigns-project-configurations"></a>Modalità di assegnazione delle configurazioni di progetto in Visual Studio

Quando si definisce una nuova configurazione di soluzione e non la si copia da una già esistente, in Visual Studio vengono usati i criteri seguenti per assegnare configurazioni di progetto predefinite. I criteri vengono valutati nell'ordine indicato.

1. Se un progetto ha *\<configuration name> \<platform name>* un nome di configurazione ( ) che corrisponde esattamente al nome della nuova configurazione della soluzione, tale configurazione viene assegnata. I nomi delle configurazioni non rispettano la distinzione tra maiuscole e minuscole.

1. Se il progetto include un nome di configurazione in cui la parte del nome corrisponde alla nuova configurazione per la soluzione, tale configurazione viene assegnata, anche se le piattaforme non coincidono.

1. Se non esiste alcuna corrispondenza, viene assegnata la prima configurazione elencata nel progetto.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Modalità di assegnazione delle configurazioni per le soluzioni in Visual Studio

Quando si crea una configurazione per il progetto (in **Gestione configurazione** scegliere **Nuovo** nel menu a discesa nella colonna **Configurazione** del progetto) e si seleziona la casella di controllo **Crea nuove configurazioni soluzione**, in Visual Studio viene cercata una configurazione con lo stesso nome per compilare il progetto per ogni piattaforma supportata. In alcuni casi, le configurazioni di soluzione esistenti vengono rinominate o ne vengono definite di nuove.

In Visual Studio vengono usati i criteri seguenti per assegnare configurazioni di soluzione.

- Se in una configurazione di progetto non è specificata una piattaforma oppure ne è specificata una sola, viene trovata o aggiunta una configurazione per la soluzione il cui nome corrisponde a quello della nuova configurazione di progetto. Il nome predefinito di questa configurazione di soluzione non include un nome di piattaforma. assume il formato *\<project configuration name>* .

- Se un progetto supporta più piattaforme, verrà trovata o aggiunta una configurazione per la soluzione per ogni piattaforma supportata. Il nome di ogni configurazione di soluzione include sia il nome *\<project configuration name> \<platform name>* della configurazione del progetto che il nome della piattaforma e ha il formato .

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Creare un'applicazione](../ide/walkthrough-building-an-application.md)
- [Compilare](../ide/compiling-and-building-in-visual-studio.md)
- [Soluzioni e progetti](../ide/solutions-and-projects-in-visual-studio.md)
- [Riferimenti alla compilazione in C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Informazioni sulle piattaforme di compilazione](understanding-build-platforms.md)
- [Build configurations (Visual Studio per Mac)](/visualstudio/mac/configurations) (Compilare configurazioni)
