---
title: Panoramica di Strumenti di Visual Studio per Office Runtime
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 31d2244796282aaad56011d5b9963232d3438ce9
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253992"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Panoramica di Strumenti di Visual Studio per Office Runtime
  Per eseguire soluzioni create usando gli strumenti di sviluppo Microsoft Office in Visual Studio, Visual Studio 2010 Tools per Office Runtime deve essere installato nei computer degli utenti finali. Per altre informazioni, vedere [Procedura: Installare la Strumenti di Visual Studio per Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Visual Studio 2010 Tools per Office Runtime è costituito da due componenti principali:

- Le estensioni di Office per .NET Framework. Questi componenti sono assembly gestiti che forniscono il livello di comunicazione tra la soluzione e l'applicazione di Microsoft Office. Per ulteriori informazioni, vedere informazioni [sulle estensioni di Office per la .NET Framework](#officeextensions).

- Il caricatore di soluzioni Office. Questo componente è un set di DLL non gestite che le applicazioni di Office usano per caricare il runtime e le soluzioni. Per ulteriori informazioni, vedere informazioni [sul caricatore di soluzioni Office](#UnmanagedLoader).

  È possibile installare il runtime in numerose modalità diverse. A seconda della configurazione del computer, al momento dell'installazione del runtime vengono installati componenti di runtime diversi. Per ulteriori informazioni, vedere [strumenti di Visual Studio per gli scenari di installazione di Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

## <a name="officeextensions"></a>Informazioni sulle estensioni di Office per la .NET Framework
 Visual Studio 2010 Tools per Office Runtime include le estensioni di Office per il .NET Framework 3,5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e versioni successive. Nelle soluzioni destinate a ciascuna versione di .NET Framework vengono usate le estensioni appropriate per la versione interessata.

 Queste estensioni sono costituite da assembly usati dalle soluzioni per automatizzare ed estendere le applicazioni di Office. Quando si crea un progetto di Office, in Visual Studio vengono automaticamente aggiunti riferimenti agli assembly usati per il tipo di progetto e .NET Framework di destinazione del progetto. Per ulteriori informazioni sugli assembly nelle estensioni di Office, vedere [assembly nel strumenti di Visual Studio per Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

### <a name="design-differences-in-the-office-extensions"></a>Differenze di progettazione nelle estensioni di Office
 La maggior parte dei tipi usati nelle estensioni di Office per .NET Framework 3.5 sono classi. Si tratta delle stesse classi incluse nelle versioni precedenti di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. La maggior parte dei tipi usati nelle estensioni Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive è costituita invece da interfacce. Ad esempio, quando si usa [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, i tipi <xref:Microsoft.Office.Tools.Excel.Worksheet> e <xref:Microsoft.Office.Tools.Word.Document> sono interfacce anziché classi.

 Nella maggior parte dei casi, il codice che si scrive nelle soluzioni Office è lo stesso sia che la soluzione venga destinata a .NET Framework 3.5 o a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Tuttavia, alcune funzionalità richiedono codice diverso quando si ha come destinazione versioni diverse di .NET Framework. Per ulteriori informazioni, vedere [eseguire la migrazione di soluzioni Office a .NET Framework 4 o versione successiva](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Interfacce nelle estensioni di Office per .NET Framework 4 o versione successiva
 La maggior parte delle interfacce nelle estensioni Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive non è studiata per essere implementata dal codice utente. Le uniche interfacce che è possibile implementare direttamente hanno nomi che iniziano con la lettera **I**, ad esempio <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>.

 Tutte le interfacce che non iniziano con la lettera **i** sono implementate internamente da Visual Studio 2010 Tools per Office Runtime e queste interfacce potrebbero cambiare nelle versioni future. Per creare oggetti che implementano tali interfacce, usare i metodi forniti dall'oggetto `Globals.Factory` nel progetto. Ad esempio, per ottenere un oggetto che implementa l'interfaccia <xref:Microsoft.Office.Tools.Excel.SmartTag>, usare il metodo `Globals.Factory.CreateSmartTag`. Per altre informazioni su `Globals.Factory`, vedere [accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Abilitare l'equivalenza dei tipi e i tipi incorporati nei progetti destinati a .NET Framework 4 o versione successiva
 Poiché il modello a oggetti delle estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva è basato su interfacce, è possibile usare la funzionalità di equivalenza dei tipi sia in Visual C# che in Visual Basic in Visual Studio per incorporare nella soluzione informazioni sul tipo da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Questa funzionalità consente alle soluzioni Office e a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] di eseguire il controllo della versione in modo indipendente. Se ad esempio la soluzione usa l'interfaccia <xref:Microsoft.Office.Tools.Word.Document> come tipo incorporato e la versione successiva del runtime aggiunge membri all'interfaccia <xref:Microsoft.Office.Tools.Word.Document> , la soluzione funzionerà comunque con la versione successiva del runtime. Se la soluzione non usa l'interfaccia <xref:Microsoft.Office.Tools.Word.Document> come tipo incorporato, non funzionerà più con la versione successiva del runtime.

 Per impostazione predefinita, la funzionalità di equivalenza dei tipi non è abilitata quando si crea un progetto di Office destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva. Se si desidera abilitare tale funzionalità, impostare la proprietà **Incorpora tipi di interoperabilità** di uno qualsiasi dei seguenti riferimenti all'assembly nel progetto su **True**:

- Microsoft.Office.Tools.dll

- Microsoft.Office.Tools.Common.dll

- Microsoft.Office.Tools.Excel.dll

- Microsoft.Office.Tools.Outlook.dll

- Microsoft.Office.Tools.Word.dll

  Dopo avere effettuato tale modifica, le informazioni sul tipo per tutti i tipi di runtime usati dal progetto vengono incorporate nell'assembly della soluzione quando il progetto viene compilato. In fase di esecuzione, la soluzione usa tali informazioni sul tipo incorporato, anziché le informazioni sui tipi negli assembly a cui si fa riferimento.

## <a name="UnmanagedLoader"></a>Informazioni sul caricatore di soluzioni Office
 Il runtime di Visual Studio Tools per Office include molte DLL non gestite che nelle applicazioni di Office servono a caricare il runtime e le soluzioni Office. Anche se non si lavora mai direttamente con queste DLL, conoscerne lo scopo può permettere di comprendere meglio l'architettura delle soluzioni Office.

 Per informazioni sull'uso di questi componenti durante il processo di caricamento, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md) e [architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="vstoeedll"></a>vstoee.dll
 Quando un utente apre una personalizzazione a livello di documento o avvia un componente aggiuntivo VSTO, l'applicazione di Office effettua la chiamata a *VSTOEE. dll* per eseguire le attività necessarie [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]per caricare.

 *VSTOEE. dll* verifica che [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] venga caricata la versione corretta di per la soluzione e la versione installata di Office. Sebbene sia [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] possibile installare più versioni di nello stesso computer, viene installata solo un'istanza di *VSTOEE. dll* alla volta. Si tratta del file *VSTOEE. dll* incluso nella versione più recente del runtime installato nel computer. Per ulteriori informazioni sulle diverse versioni di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che possono essere utilizzate per altre soluzioni, vedere [eseguire soluzioni in versioni diverse di Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

### <a name="vstoloaderdll"></a>VSTOLoader.dll
 Dopo che *VSTOEE. dll* carica la versione appropriata di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], *VSTOLoader. dll* esegue la maggior parte delle operazioni necessarie per caricare l'assembly della soluzione. *VSTOLoader. dll* esegue diverse operazioni:

- Creare un dominio dell'applicazione per ogni assembly della soluzione.

- Eseguire un set di controlli di sicurezza per verificare che l'assembly della soluzione disponga delle autorizzazioni per l'esecuzione.

- Caricare la versione delle estensioni di Office per .NET Framework richiesta dalla soluzione.

  *VSTOLoader. dll* esegue anche diverse operazioni specifiche per i componenti aggiuntivi VSTO:

- Implementa l'interfaccia <xref:Extensibility.IDTExtensibility2> . <xref:Extensibility.IDTExtensibility2> è un'interfaccia COM che deve essere implementata da tutti i componenti aggiuntivi VSTO per le applicazioni di Microsoft Office. Questa interfaccia definisce i metodi chiamati dall'applicazione per comunicare con il componente aggiuntivo VSTO.

- Implementa l'interfaccia IManagedAddin. Questa interfaccia viene usata dalle applicazioni di Office per consentire il caricamento di componenti aggiuntivi VSTO. Per ulteriori informazioni, vedere [interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md).

## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Informazioni sulle versioni a 32 bit e a 64 bit del runtime
 Sono disponibili versioni separate a 64 bit e a 32 bit di Visual Studio 2010 Tools per Office Runtime. Tali versioni del runtime vengono usate per eseguire soluzioni in edizioni di Office a 64 bit e a 32 bit. Nella tabella seguente viene illustrata la versione del runtime richiesta per ogni combinazione di Windows e Office.

|Edizione di Windows|Edizione di Microsoft Office|Versione richiesta del runtime di Visual Studio Tools per Office|
|------------------------|---------------------------------|--------------------------------------------------------------------|
|32 bit|32 bit|32 bit|
|64 bit|32 bit|64 bit|
|64 bit|64 bit|64 bit|

 Quando si installa Office, la versione richiesta di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] viene installata insieme a Office. Ad esempio, quando si installa l'edizione a 64 bit di Office in una versione a 64 bit di Windows, viene installata anche la versione a 64 bit di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Per ulteriori informazioni sull'installazione di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] con Office, vedere [strumenti di Visual Studio per gli scenari di installazione di Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

 La versione a 64 bit di Office può eseguire anche soluzioni Office create mediante modelli di progetto per Microsoft Office System 2007 in Visual Studio 2008. Non è tuttavia in grado di eseguire soluzioni Office create mediante modelli di progetto per Microsoft Office 2003 in Visual Studio 2008 né soluzioni Office create usando Visual Studio 2005. Per altre informazioni, vedere [eseguire soluzioni in versioni diverse di Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Ripristinare Visual Studio 2010 Tools per Office Runtime
 Se è necessario ripristinare il runtime, aprire **Programmi e funzionalità** o **Installazione applicazioni** nel Pannello di controllo, selezionare **Microsoft Visual Studio 2010 Tools per Office Runtime** nell'elenco di programmi, quindi fare clic su **Disinstalla**. Il programma di installazione che viene eseguito consente di ripristinare il runtime. Se si fa clic su **Cambia**, non viene fornita un'opzione per ripristinare il runtime.

## <a name="see-also"></a>Vedere anche
- [Scenari di installazione di Strumenti di Visual Studio per Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Assembly nel Strumenti di Visual Studio per Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
- [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Procedura: Creazione di progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Aggiornare ed eseguire la migrazione di soluzioni Office](../vsto/upgrading-and-migrating-office-solutions.md)
