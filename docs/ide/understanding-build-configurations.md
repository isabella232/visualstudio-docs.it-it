---
title: Informazioni sulle configurazioni della build
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a37d4fa5dc92253b94dc64590c9df5fec7703ceb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904165"
---
# <a name="understand-build-configurations"></a>Informazioni sulle configurazioni della build

Sono necessarie configurazioni di compilazione quando è necessario compilare i progetti con impostazioni diverse. Ad esempio, **Debug** e **Release** sono configurazioni e diverse opzioni del compilatore vengono utilizzate di conseguenza durante la compilazione.  Una configurazione è attiva ed è indicata nella barra dei comandi nella parte superiore dell'IDE.

![Configurazione attiva](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Build configurations in Visual Studio for Mac](/visualstudio/mac/configurations) (Compilazione di configurazioni in Visual Studio for Mac).

La configurazione e il controllo della piattaforma in cui vengono archiviati i file di output compilati. In genere, quando Visual Studio compila il progetto, l'output viene inserito in una sottocartella di progetto denominata con la configurazione attiva (ad esempio, *bin/Debug/x86*), ma è possibile modificarlo.

È possibile creare configurazioni di compilazione personalizzate a livello di soluzione e di progetto. La configurazione della soluzione determina quali progetti sono inclusi nella compilazione quando tale configurazione è attiva. Verranno compilati solo i progetti specificati nella configurazione di soluzione attiva. Se in Configuration Manager sono selezionate più piattaforme di destinazione, vengono compilati tutti i progetti che si applicano a tale piattaforma. La configurazione del progetto determina quali impostazioni di compilazione e le opzioni del compilatore vengono utilizzate quando si compila il progetto.

Per creare, selezionare, modificare o eliminare una configurazione, è possibile usare **Gestione configurazione**. Per aprirlo, nella barra dei menu scegliere **Gestione configurazione di compilazione** > **Configuration Manager**o semplicemente **digitare Configurazione** nella casella di ricerca. È inoltre possibile usare l'elenco **Configurazioni soluzione** sulla barra degli strumenti **Standard** per selezionare una configurazione o aprire **Gestione configurazione**.

![Gestione configurazione](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Se non è possibile trovare le impostazioni di configurazione della soluzione [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] sulla barra degli strumenti e non è possibile accedere a Configuration **Manager**, è possibile che vengano applicate le impostazioni di sviluppo. Per altre informazioni, vedere [Procedura: Gestire configurazioni di compilazione applicando le impostazioni di Visual Basic Developer](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Per impostazione predefinita, le configurazioni **Debug** e [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Release** sono incluse nei progetti creati utilizzando i modelli. Una configurazione **di debug** supporta il debug di un'app e una configurazione **di rilascio** compila una versione dell'app che può essere distribuita. Per altre informazioni, vedere [Procedura: Impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md). È inoltre possibile creare configurazioni personalizzate per progetti e soluzioni. Per altre informazioni, vedere [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Configurazioni di soluzioni

In una configurazione per la soluzione viene specificato il modo in cui i progetti di una soluzione devono essere compilati e distribuiti. Per modificare una configurazione per la soluzione o per definirne una nuova, in **Gestione configurazione**, sotto la voce **Configurazione soluzione attiva** scegliere **Modifica** o **Nuovo**.

Ogni voce nella casella **Contesti progetto** di una configurazione per la soluzione rappresenta un progetto nella soluzione. Per ogni combinazione di **Configurazione soluzione attiva** e **Piattaforma soluzione attiva**, è possibile definire il modo in cui ogni progetto viene usato. Per altre informazioni sulle piattaforme per la soluzione, vedere [Informazioni sulle piattaforme di compilazione](../ide/understanding-build-platforms.md).

Quando si definisce una nuova configurazione per la soluzione e si seleziona la casella di controllo **Crea nuove configurazioni progetto**, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene assegnata automaticamente la nuova configurazione a tutti i progetti. In modo analogo, quando si definisce una nuova configurazione per la soluzione e si seleziona la casella di controllo **Crea nuove piattaforme progetto**, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene assegnata automaticamente la nuova configurazione a tutti i progetti. Inoltre, se si aggiunge un progetto destinato a una nuova piattaforma, in Visual Studio tale piattaforma viene aggiunta all'elenco delle piattaforme per la soluzione e assegnata a tutti i progetti. È ancora possibile modificare le impostazioni per ogni progetto.

La configurazione per la soluzione attiva fornisce anche il contesto all'IDE. Se, ad esempio, si sta lavorando a un progetto e nella configurazione per la soluzione attiva viene specificata la compilazione per un dispositivo mobile, nella **Casella degli strumenti** verranno visualizzati solo gli elementi del progetto che possono essere usati in un progetto per un dispositivo mobile.

## <a name="project-configurations"></a>Configurazioni di progetto

La configurazione e la piattaforma utilizzate insieme a un progetto per specificare le impostazioni di compilazione e le opzioni del compilatore da usare quando viene compilata. Un progetto può avere impostazioni diverse per ogni combinazione di configurazione e piattaforma. Per modificare le proprietà di un progetto, aprire il menu di scelta rapida per il progetto in **Esplora soluzioni**, quindi scegliere **Proprietà**.  Nella parte superiore della scheda **Compila** di Progettazione progetti scegliere una configurazione attiva per modificarne le impostazioni di compilazione.

![Configurazioni di Progettazione progetti](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>Creazione di più configurazioni

Quando si compila una soluzione utilizzando il comando **Compila** > **soluzione** di compilazione, Visual Studio compila solo la configurazione attiva. Tutti i progetti specificati nella configurazione della soluzione vengono compilati e l'unica configurazione di progetto compilata è quella specificata nella configurazione della soluzione attiva e nella piattaforma della soluzione attiva, visualizzata nella barra degli strumenti in Visual Studio.All projects that are specified in that solution configuration are built, and the only project configuration that's built is one specified in the active solution configuration and active solution platform, which is shown in the toolbar in Visual Studio. Ad esempio, **Debug** e **x86**. Altre configurazioni e piattaforme definite non vengono compilate.

Se si desidera compilare più configurazioni e piattaforme in un'unica azione, è possibile usare l'opzione Compila**compilazione batch** in Visual Studio.If you want to build multiple configurations and platforms in one action, you can use the **Build** > Batch Build option in Visual Studio. Per accedere a questa funzionalità, premere **CTRL**+**Q** per aprire la casella di ricerca e immettere `Batch build`. La compilazione batch non è disponibile per tutti i tipi di progetto. Vedere [Procedura: Creare più configurazioni contemporaneamente.](how-to-build-multiple-configurations-simultaneously.md)

## <a name="how-visual-studio-assigns-project-configurations"></a>Modalità di assegnazione delle configurazioni di progetto in Visual Studio

Quando si definisce una nuova configurazione di soluzione e non la si copia da una già esistente, in Visual Studio vengono usati i criteri seguenti per assegnare configurazioni di progetto predefinite. I criteri vengono valutati nell'ordine indicato.

1. Se un progetto ha*\< \< *un nome di configurazione ( nome configurazione> nome di piattaforma>) che corrisponde esattamente al nome della nuova configurazione di soluzione, tale configurazione viene assegnata. I nomi delle configurazioni non rispettano la distinzione tra maiuscole e minuscole.

1. Se il progetto include un nome di configurazione in cui la parte del nome corrisponde alla nuova configurazione per la soluzione, tale configurazione viene assegnata, anche se le piattaforme non coincidono.

1. Se non esiste alcuna corrispondenza, viene assegnata la prima configurazione elencata nel progetto.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Modalità di assegnazione delle configurazioni per le soluzioni in Visual Studio

Quando si crea una configurazione per il progetto (in **Gestione configurazione** scegliere **Nuovo** nel menu a discesa nella colonna **Configurazione** del progetto) e si seleziona la casella di controllo **Crea nuove configurazioni soluzione**, in Visual Studio viene cercata una configurazione con lo stesso nome per compilare il progetto per ogni piattaforma supportata. In alcuni casi, le configurazioni di soluzione esistenti vengono rinominate o ne vengono definite di nuove.

In Visual Studio vengono usati i criteri seguenti per assegnare configurazioni di soluzione.

- Se in una configurazione di progetto non è specificata una piattaforma oppure ne è specificata una sola, viene trovata o aggiunta una configurazione per la soluzione il cui nome corrisponde a quello della nuova configurazione di progetto. Il nome predefinito di questa configurazione di soluzione non include un nome di piattaforma. accetta il * \<nome *di configurazione del progetto del modulo>.

- Se un progetto supporta più piattaforme, verrà trovata o aggiunta una configurazione per la soluzione per ogni piattaforma supportata. Il nome di ogni configurazione di soluzione include sia il nome della configurazione del progetto che il nome della piattaforma e il nome della configurazione del * \<progetto> \<nome di piattaforma>*.

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: compilare un'applicazioneWalkthrough: Build an application](../ide/walkthrough-building-an-application.md)
- [Compilazione e creazione](../ide/compiling-and-building-in-visual-studio.md)
- [Soluzioni e progetti](../ide/solutions-and-projects-in-visual-studio.md)
- [Riferimenti alla compilazione in C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Informazioni sulle piattaforme di compilazioneUnderstanding build platforms](understanding-build-platforms.md)
- [Build configurations (Visual Studio per Mac)](/visualstudio/mac/configurations) (Compilare configurazioni)
