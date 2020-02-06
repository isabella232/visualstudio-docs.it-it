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
ms.openlocfilehash: 6b472ca78d36247a76bf397989f48e04230ccd7d
ms.sourcegitcommit: b2fc9ac7d73c847508f6ed082bed026476bb3955
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2020
ms.locfileid: "77027621"
---
# <a name="understand-build-configurations"></a>Informazioni sulle configurazioni della build

Sono necessarie configurazioni di compilazione quando è necessario compilare i progetti con impostazioni diverse. Ad esempio, il **debug** e il **rilascio** sono configurazioni e le diverse opzioni del compilatore vengono usate di conseguenza durante la compilazione.  Una configurazione è attiva ed è indicata nella barra dei comandi nella parte superiore dell'IDE.

![Configurazione attiva](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Build configurations in Visual Studio for Mac](/visualstudio/mac/configurations) (Compilazione di configurazioni in Visual Studio for Mac).

La configurazione e il controllo della piattaforma in cui vengono archiviati i file di output compilati. In genere, quando Visual Studio compila il progetto, l'output viene inserito in una sottocartella del progetto denominata con la configurazione attiva (ad esempio *bin/debug/x86*), ma è possibile modificarla.

È possibile creare configurazioni di compilazione personalizzate a livello di soluzione e di progetto. La configurazione della soluzione determina i progetti inclusi nella compilazione quando tale configurazione è attiva. Verranno compilati solo i progetti specificati nella configurazione della soluzione attiva. La configurazione del progetto determina le impostazioni di compilazione e le opzioni del compilatore utilizzate quando si compila il progetto.

Per creare, selezionare, modificare o eliminare una configurazione, è possibile usare **Gestione configurazione**. Per aprirlo, nella barra dei menu scegliere **Compilazione** > **Gestione configurazione** oppure digitare **configurazione** nella casella di ricerca. È inoltre possibile usare l'elenco **Configurazioni soluzione** sulla barra degli strumenti **Standard** per selezionare una configurazione o aprire **Gestione configurazione**.

![Gestione configurazione](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Se le impostazioni di configurazione della soluzione non vengono trovate sulla barra degli strumenti oppure se non è possibile accedere a **Gestione configurazione**, è possibile che siano applicate le impostazioni di sviluppo di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Per altre informazioni, vedere [Procedura: Gestire configurazioni di compilazione applicando le impostazioni di Visual Basic Developer](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Per impostazione predefinita, le configurazioni di **debug** e **rilascio** sono incluse nei progetti creati tramite modelli di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Una configurazione di **debug** supporta il debug di un'app e una **configurazione di versione compila** una versione dell'app che può essere distribuita. Per altre informazioni, vedere [Procedura: Impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md). È inoltre possibile creare configurazioni personalizzate per progetti e soluzioni. Per altre informazioni, vedere [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Configurazioni di soluzioni

In una configurazione per la soluzione viene specificato il modo in cui i progetti di una soluzione devono essere compilati e distribuiti. Per modificare una configurazione per la soluzione o per definirne una nuova, in **Gestione configurazione**, sotto la voce **Configurazione soluzione attiva** scegliere **Modifica** o **Nuovo**.

Ogni voce nella casella **Contesti progetto** di una configurazione per la soluzione rappresenta un progetto nella soluzione. Per ogni combinazione di **Configurazione soluzione attiva** e **Piattaforma soluzione attiva**, è possibile definire il modo in cui ogni progetto viene usato. Per altre informazioni sulle piattaforme per la soluzione, vedere [Informazioni sulle piattaforme di compilazione](../ide/understanding-build-platforms.md).

Quando si definisce una nuova configurazione per la soluzione e si seleziona la casella di controllo **Crea nuove configurazioni progetto**, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene assegnata automaticamente la nuova configurazione a tutti i progetti. In modo analogo, quando si definisce una nuova configurazione per la soluzione e si seleziona la casella di controllo **Crea nuove piattaforme progetto**, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene assegnata automaticamente la nuova configurazione a tutti i progetti. Inoltre, se si aggiunge un progetto destinato a una nuova piattaforma, in Visual Studio tale piattaforma viene aggiunta all'elenco delle piattaforme per la soluzione e assegnata a tutti i progetti. È ancora possibile modificare le impostazioni per ogni progetto.

La configurazione per la soluzione attiva fornisce anche il contesto all'IDE. Se, ad esempio, si sta lavorando a un progetto e nella configurazione per la soluzione attiva viene specificata la compilazione per un dispositivo mobile, nella **Casella degli strumenti** verranno visualizzati solo gli elementi del progetto che possono essere usati in un progetto per un dispositivo mobile.

## <a name="project-configurations"></a>Configurazioni di progetto

La configurazione e la piattaforma di destinazione di un progetto vengono utilizzate insieme per specificare le impostazioni di compilazione e le opzioni del compilatore da utilizzare durante la compilazione. Un progetto può avere impostazioni diverse per ogni combinazione di configurazione e piattaforma. Per modificare le proprietà di un progetto, aprire il menu di scelta rapida del progetto in **Esplora soluzioni**, quindi scegliere **Proprietà**.  Nella parte superiore della scheda **compilazione** di progettazione progetti scegliere una configurazione attiva per modificare le impostazioni di compilazione.

![Configurazioni di progettazione progetti](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="how-visual-studio-assigns-project-configurations"></a>Modalità di assegnazione delle configurazioni di progetto in Visual Studio

Quando si definisce una nuova configurazione di soluzione e non la si copia da una già esistente, in Visual Studio vengono usati i criteri seguenti per assegnare configurazioni di progetto predefinite. I criteri vengono valutati nell'ordine indicato.

1. Se il nome di configurazione ( *\<nome configurazione> \<nome piattaforma>* ) di un progetto corrisponde esattamente al nome della nuova configurazione per la soluzione, viene assegnata la configurazione specifica. I nomi delle configurazioni non rispettano la distinzione tra maiuscole e minuscole.

1. Se il progetto include un nome di configurazione in cui la parte del nome corrisponde alla nuova configurazione per la soluzione, tale configurazione viene assegnata, anche se le piattaforme non coincidono.

1. Se non esiste alcuna corrispondenza, viene assegnata la prima configurazione elencata nel progetto.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Modalità di assegnazione delle configurazioni per le soluzioni in Visual Studio

Quando si crea una configurazione per il progetto (in **Gestione configurazione** scegliere **Nuovo** nel menu a discesa nella colonna **Configurazione** del progetto) e si seleziona la casella di controllo **Crea nuove configurazioni soluzione**, in Visual Studio viene cercata una configurazione con lo stesso nome per compilare il progetto per ogni piattaforma supportata. In alcuni casi, le configurazioni di soluzione esistenti vengono rinominate o ne vengono definite di nuove.

In Visual Studio vengono usati i criteri seguenti per assegnare configurazioni di soluzione.

- Se in una configurazione di progetto non è specificata una piattaforma oppure ne è specificata una sola, viene trovata o aggiunta una configurazione per la soluzione il cui nome corrisponde a quello della nuova configurazione di progetto. Il nome predefinito di tale configurazione di soluzione non include un nome di piattaforma e pertanto assume il formato *\<nome configurazione di progetto>* .

- Se un progetto supporta più piattaforme, verrà trovata o aggiunta una configurazione per la soluzione per ogni piattaforma supportata. Il nome di ogni configurazione di soluzione include sia il nome della configurazione di progetto sia il nome della piattaforma e assume il formato *\<nome configurazione di progetto> \<nome piattaforma>* .

## <a name="see-also"></a>Vedere anche

- [Walkthrough: Building an Application](../ide/walkthrough-building-an-application.md) (Procedura dettagliata: Compilare un'applicazione)
- [Compilare](../ide/compiling-and-building-in-visual-studio.md)
- [Soluzioni e progetti](../ide/solutions-and-projects-in-visual-studio.md)
- [Riferimenti alla compilazione in C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Informazioni sulle piattaforme di compilazione](understanding-build-platforms.md)
- [Build configurations (Visual Studio per Mac)](/visualstudio/mac/configurations) (Compilare configurazioni)
