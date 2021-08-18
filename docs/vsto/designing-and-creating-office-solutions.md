---
title: Progettare e creare Office soluzioni
description: Informazioni su Visual Studio fornisce modelli di progetto che è possibile usare per creare diversi tipi di Office soluzioni.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 248fe0caba9d1fbfca34c49b63ccf7bea31ea3de
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038084"
---
# <a name="design-and-create-office-solutions"></a>Progettare e creare Office soluzioni

Visual Studio fornisce modelli di progetto che è possibile utilizzare per creare diversi tipi di soluzioni Office. In questa sezione della documentazione vengono descritti i modelli di progetto e vengono fornite informazioni aggiuntive sulla creazione di progetti di Office. Per informazioni su come implementare personalizzazioni del codice e dell'interfaccia utente dopo aver creato il progetto, vedere Sviluppare Office [soluzioni](../vsto/developing-office-solutions.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-office-projects"></a>Creare Office progetti
 Prima di iniziare, è necessario stabilire i requisiti e individuare il tipo di soluzione più adatta alle proprie esigenze. Ad esempio, se la soluzione Office deve essere eseguita ogni volta che viene usata l'applicazione, un componente aggiuntivo VSTO è più adatto per soddisfare le esigenze. Se il codice è strettamente integrato con un unico documento, creare una personalizzazione a livello di documento. Questi tipi di progetto sono disponibili come modelli di progetto Visual Studio. Per altre informazioni sui modelli Office di progetto inclusi in Visual Studio, vedere Office [panoramica dei modelli di progetto.](../vsto/office-project-templates-overview.md) Per altre informazioni su come creare progetti Office, vedere [Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 I progetti Office presentano funzionalità ed elementi di progetto diversi da altri tipi di progetti in Visual Studio. Ad esempio, quando si crea un progetto a livello di documento, il documento o cartella di lavoro nel progetto può essere aperto e modificato in Visual Studio. Per altre informazioni, vedere [Office progetti nell'ambiente Visual Studio .](../vsto/office-projects-in-the-visual-studio-environment.md)

## <a name="choose-a-net-framework-version"></a>Scegliere una .NET Framework versione
 Dopo aver selezionato il tipo di progetto che meglio soddisfa le proprie esigenze, è possibile scegliere quale versione di .NET Framework utilizzare nel processo di sviluppo. È possibile destinare le seguenti versioni di .NET Framework nei progetti di Office:

- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]

- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]

  La .NET Framework versione scelta per il progetto è necessaria nei computer degli utenti finali per l'esecuzione della soluzione. Ad esempio, se il progetto è destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , è necessario nei computer degli utenti [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] finali. In questo esempio la soluzione non verrà eseguita se nei computer degli utenti finali .NET Framework 3.5 è installato solo il .NET Framework 3.5.

  Se si esegue la migrazione di un progetto di componente aggiuntivo VSTO destinato a .NET Framework 3.5, Visual Studio modifica il framework di destinazione del progetto impostandolo su [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva, a seconda della versione di Office installata.

  Dopo la modifica del framework di destinazione, tuttavia, potrebbe essere necessario modificare parte del codice nel progetto se vengono utilizzate alcune funzionalità. Per altre informazioni su come modificare il framework di destinazione, vedere [Procedura: Impostare](../ide/visual-studio-multi-targeting-overview.md)come destinazione una versione del .NET Framework . Per altre informazioni sulle modifiche che potrebbe essere necessario apportare nel progetto, vedere Eseguire la migrazione di Office soluzioni al .NET Framework [4 o versioni successive.](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)

  Se Visual Studio modifica il .NET Framework di destinazione per il progetto e si usa ClickOnce per distribuire la soluzione, assicurarsi di selezionare anche  la versione corrispondente del .NET Framework nella finestra di dialogo Prerequisiti. Questa selezione non viene modificata automaticamente quando si modifica il framework di destinazione per il progetto. Per altre informazioni, vedere [Procedura: Installare i prerequisiti](/previous-versions/bb608608(v=vs.110))nei computer degli utenti finali per eseguire Office soluzioni .

> [!NOTE]
> Non è possibile usare .NET Framework 3.5 o versioni precedenti nei progetti Office creati tramite [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]. I progetti di Office create mediante [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] richiedono funzionalità che sono state introdotte in [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>Comprendere quando sono Office più personali nei computer degli utenti finali
 Per impostazione predefinita, non è necessario installare Office assembly di interoperabilità primari (PIA) nei computer degli utenti finali se la proprietà Incorpora tipi di interoperabilità di ogni riferimento Office PIA nel progetto è impostata su **True**, che è il valore predefinito.  In questo scenario, le informazioni sul tipo per i tipi di assembly di interoperabilità primari utilizzati dalla soluzione vengono incorporate nell'assembly della soluzione quando si compila il progetto. In fase di runtime, le informazioni sul tipo incorporate vengono utilizzate al posto degli assembly di interoperabilità primari per chiamare il modello a oggetti COM dell'applicazione di Office. Per altre informazioni sul modo in cui i tipi dagli assembly di interoperabilità primari vengono incorporati nella soluzione, vedere Equivalenza dei tipi [e tipi di interoperabilità incorporati](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).

 Se  la proprietà Incorpora tipi di interoperabilità di ogni riferimento Office PIA nel progetto è impostata su **False**, gli assembly di interoperabilità primari Office devono essere installati e registrati nella Global Assembly Cache in ogni computer dell'utente finale che esegue la soluzione. Nella maggior parte dei casi, gli assembly di interoperabilità primari vengono installati per impostazione predefinita con Office, ma è anche possibile includere l'assembly di interoperabilità primario ridistribuibile come prerequisito per la soluzione. Per altre informazioni, vedere Office [prerequisiti della soluzione per la distribuzione](/previous-versions/bb608617(v=vs.110)).

### <a name="understand-the-client-profile"></a>Informazioni sul profilo client
 .NET Framework Client Profile è un sottoinsieme della versione completa di .NET Framework. È possibile scegliere .NET Framework Client Profile se è necessario utilizzare solo le funzionalità client di .NET Framework e si desidera fornire l'esperienza di distribuzione più veloce per la soluzione Office. Per altre informazioni, vedere .NET Framework [client](/dotnet/framework/deployment/client-profile).

 Quando si crea un progetto Office destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)],  [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] è la destinazione predefinita. Se si vuole sviluppare per la versione [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] completa, è necessario impostare questa opzione dopo la creazione del progetto. Per altre informazioni, vedere [Procedura: Scegliere una versione di .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Creare soluzioni per l'edizione a 64 bit di Microsoft Office
 Microsoft Office è disponibile nelle edizioni a 64 bit e a 32 bit. Per creare Office che possono essere eseguite in entrambe le edizioni, l'impostazione di destinazione della piattaforma per il progetto deve essere impostata su **Qualsiasi CPU.** Questo è il valore predefinito per i progetti Office. Per altre informazioni, vedere [Compilare Office soluzioni](../vsto/building-office-solutions.md).

 Sono disponibili versioni a 32 e 64 bit separate di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che vengono utilizzate per le edizioni a 64 bit e a 32 bit di Microsoft Office. Per altre informazioni, vedere panoramica [Visual Studio Tools per Office runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-office-solutions"></a>Assembly in Office soluzioni
 Quando si crea un progetto di Office mediante gli strumenti di sviluppo per Office in Visual Studio, il codice scritto viene compilato in un assembly. L'assembly viene distribuito in un server condiviso o in una directory nel computer client.

 Gli assembly nelle soluzioni Office vengono caricati da un'applicazione di Office. Dopo che l'assembly viene caricato, il codice nell’assembly può rispondere agli eventi generati nell'applicazione (ad esempio quando un utente fa clic su una voce di menu). Il codice nell’assembly può inoltre effettuare chiamate nel modello a oggetti per automatizzare ed estendere l'applicazione e può utilizzare una qualsiasi delle classi in [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]. Per altre informazioni, vedere [Architettura delle personalizzazioni](../vsto/architecture-of-document-level-customizations.md) a livello di documento e Architettura VSTO [componenti aggiuntivi](../vsto/architecture-of-vsto-add-ins.md).

 Le soluzioni Office utilizzano i manifesti di distribuzione e di applicazione per identificare l'assembly. I manifesti contengono informazioni su nome, versione e percorso dell'assembly, per cui l'applicazione può trovare, collegare ed eseguire l'assembly corretto. Per altre informazioni, vedere [Manifesti dell'applicazione](../vsto/application-and-deployment-manifests-in-office-solutions.md)e della distribuzione in Office soluzioni .

 I progetti a livello di documento includono un documento oltre a un assembly. Il documento agisce come front-end dell'applicazione ed è il luogo in cui avviene l'interazione dell’utente. Ogni documento può avere un solo assembly principale del progetto associato. Tuttavia, più documenti possono puntare allo stesso assembly.

 Gli assembly nei progetti a livello di documento non sono incorporati nel documento, ma vengono archiviati in una posizione diversa e sono identificati dal manifesto di applicazione del documento.

## <a name="security-considerations-for-assemblies"></a>Considerazioni sulla sicurezza per gli assembly
 Perché una soluzione Office venga eseguita in un computer, gli assembly utilizzati dalla soluzione devono essere attendibili per l'esecuzione. Per altre informazioni sulla sicurezza, vedere [Soluzioni Office sicurezza](../vsto/securing-office-solutions.md).

 Per impostazione predefinita, l'assembly della soluzione e tutti gli assembly di riferimento che si trovano nella cartella di output del progetto sono attendibili per l'esecuzione nel computer di sviluppo quando si compila il progetto. Per altre informazioni, vedere [Compilare Office soluzioni](../vsto/building-office-solutions.md).

 Per motivi di sicurezza, è consigliabile creare progetti nel computer locale anziché svilupparli in un percorso condiviso. Per altre informazioni, vedere [Sviluppo collaborativo di Office soluzioni](../vsto/collaborative-development-of-office-solutions.md).

## <a name="referenced-assemblies"></a>Assembly di riferimento
 L'assembly può fare riferimento ad altri assembly elencati nei riferimenti del progetto. Tuttavia, un assembly del progetto a livello di documento non può fare riferimento a un altro assembly del progetto a livello di documento.

## <a name="see-also"></a>Vedi anche
- [Office dei modelli di progetto](../vsto/office-project-templates-overview.md)
- [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office progetti nell'ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)
- [Proprietà nei Office progetto](../vsto/properties-in-office-projects.md)
- [Eseguire soluzioni in versioni diverse di Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
- [Procedura: Impostare come destinazione Office applicazioni tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Manifesti dell'applicazione e della distribuzione Office soluzioni](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Procedura: Configurare le informazioni di configurazione per una Office soluzione](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)
- [Usare Office funzionalità all'interno di Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
- [Attività comuni nella programmazione Office](../vsto/common-tasks-in-office-programming.md)
- [Sviluppare Office soluzioni](../vsto/developing-office-solutions.md)
- [Architettura delle Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)