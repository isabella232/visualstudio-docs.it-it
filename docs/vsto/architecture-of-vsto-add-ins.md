---
title: Architettura dei componenti aggiuntivi VSTO
description: VSTO I componenti aggiuntivi creati in Visual Studio hanno funzionalità architetturali che evidenziano stabilità e sicurezza e consentono loro di lavorare a stretto contatto con Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- architecture [Office development in Visual Studio], application-level add-ins
- vstoee.dll
- application-level add-ins [Office development in Visual Studio], architecture
- add-ins [Office development in Visual Studio], architecture
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a8c192d9fb6c5f102247f0b38f412b94e3bdb5e6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059920"
---
# <a name="architecture-of-vsto-add-ins"></a>Architettura dei componenti aggiuntivi VSTO
  I componenti aggiuntivi VSTO creati mediante gli strumenti di sviluppo per Office disponibili in Visual Studio hanno caratteristiche correlate all'architettura che accentuano stabilità e sicurezza e che ne permettono l'integrazione con Microsoft Office. Questo argomento descrive gli aspetti seguenti dei componenti aggiuntivi VSTO:

- [Informazioni VSTO componenti aggiuntivi](#UnderstandingAddIns)

- [Elementi dei componenti aggiuntivi VSTO](#AddinComponents)

- [Funzionamento dei componenti aggiuntivi VSTO con applicazioni di Microsoft Office](#HowAddinsWork)

  [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

  Per informazioni generali sulla creazione VSTO componenti aggiuntivi, vedere Office [solutions development overview &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) e Get started programming VSTO [Add-ins](../vsto/getting-started-programming-vsto-add-ins.md).

## <a name="understand-vsto-add-ins"></a><a name="UnderstandingAddIns"></a>Informazioni VSTO componenti aggiuntivi
 Quando si usano gli strumenti di sviluppo Office in Visual Studio per compilare un componente aggiuntivo VSTO, si crea un assembly di codice gestito caricato da un'applicazione Microsoft Office codice. Dopo il caricamento dell'assembly, il componente aggiuntivo VSTO può rispondere agli eventi generati nell'applicazione, ad esempio quando un utente fa clic su una voce di menu. Il componente aggiuntivo VSTO può anche effettuare chiamate nel modello a oggetti per automatizzare ed estendere l'applicazione e può usare una qualsiasi delle classi in [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].

 L'assembly comunica con i componenti COM dell'applicazione tramite l'assembly di interoperabilità primario dell'applicazione. Per altre informazioni, vedere Office assembly di [interoperabilità](../vsto/office-primary-interop-assemblies.md) primari [e Office di sviluppo di ](../vsto/office-solutions-development-overview-vsto.md)soluzioni &#40;VSTO&#41;.

 Se sono installati più componenti aggiuntivi VSTO per un'applicazione, ognuno viene caricato in un dominio dell'applicazione diverso. Questo significa che il comportamento errato di un componente aggiuntivo VSTO non può causare errori in altri componenti aggiuntivi VSTO. In tal modo, viene inoltre garantito che, alla chiusura dell'applicazione, tutti gli assembly del componente aggiuntivo VSTO vengono scaricati dalla memoria. Per altre informazioni sui domini applicazione, vedere [Domini applicazione](/dotnet/framework/app-domains/application-domains).

> [!NOTE]
> I componenti aggiuntivi VSTO creati mediante gli strumenti di sviluppo per Office disponibili in Visual Studio sono progettati per essere usati solo quando l'applicazione di Microsoft Office host viene avviata da un utente finale. Se l'applicazione viene avviata a livello di codice, ad esempio usando l'automazione, il componente aggiuntivo VSTO potrebbe non funzionare nel modo previsto.

## <a name="components-of-vsto-add-ins"></a><a name="AddinComponents"></a>Componenti di VSTO componenti aggiuntivi
 Anche se l'assembly del componente aggiuntivo VSTO è l'elemento principale, esistono numerosi altri elementi che svolgono un ruolo importante in relazione al modo in cui le applicazioni di Microsoft Office individuano e caricano componenti aggiuntivi VSTO.

### <a name="registry-entries"></a>Voci del Registro di sistema
 Le applicazioni di Microsoft Office individuano i componenti aggiuntivi VSTO cercando un set di voci del Registro di sistema. Per un elenco completo delle voci del Registro di sistema usate VSTO componenti aggiuntivi, vedere Voci del Registro di sistema per VSTO [componenti aggiuntivi](../vsto/registry-entries-for-vsto-add-ins.md).

 Quando si compila la soluzione, Visual Studio crea tutte le voci del Registro di sistema nel computer di sviluppo così da poter eseguire il componente aggiuntivo VSTO ed effettuarne il debug. Per altre informazioni, vedere [Compilare Office soluzioni](../vsto/building-office-solutions.md).

 Se si usa ClickOnce per distribuire la soluzione, il programma di installazione generato dal processo di pubblicazione crea automaticamente le chiavi del Registro di sistema nel computer dell'utente finale. Per altre informazioni, vedere [Deploy an Office solution by using ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

### <a name="deployment-manifest-and-application-manifest"></a>Manifesto della distribuzione e manifesto dell'applicazione
 I componenti aggiuntivi VSTO usano manifesti di distribuzione e dell'applicazione per identificare e caricare la versione più aggiornata dell'assembly del componente aggiuntivo VSTO. Il manifesto della distribuzione fa riferimento al manifesto dell'applicazione corrente. Il manifesto dell'applicazione fa riferimento all'assembly del componente aggiuntivo VSTO e specifica la classe del punto di ingresso da eseguire nell'assembly. Per altre informazioni, vedere [Manifesti dell'applicazione](../vsto/application-and-deployment-manifests-in-office-solutions.md)e della distribuzione in Office soluzioni .

### <a name="visual-studio-tools-for-office-runtime"></a>Runtime di Visual Studio Tools per Office
 Per eseguire VSTO componenti aggiuntivi creati usando gli strumenti di sviluppo Office in Visual Studio, nei computer degli utenti finali deve essere [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] installato . Il runtime include componenti non gestiti e un set di assembly gestiti. I componenti non gestiti caricano l'assembly del componente aggiuntivo VSTO. Questi assembly gestiti forniscono il modello a oggetti usato dal codice del componente aggiuntivo VSTO per automatizzare ed estendere l'applicazione host.

 Per altre informazioni, vedere panoramica Visual Studio Tools per Office [runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="how-vsto-add-ins-work-with-microsoft-office-applications"></a><a name="HowAddinsWork"></a>Funzionamento VSTO componenti aggiuntivi con Microsoft Office applicazioni
 Quando un utente avvia un'applicazione di Microsoft Office, questa usa i manifesti della distribuzione e dell'applicazione per individuare e caricare la versione più recente dell'assembly del componente aggiuntivo VSTO. La figura seguente mostra l'architettura di base di questi componenti aggiuntivi VSTO.

 ![Architettura dei componenti aggiuntivi di Office 2007](../vsto/media/office07addin.png "Architettura dei componenti aggiuntivi di Office 2007")

> [!NOTE]
> Nelle soluzioni Office destinate a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], le soluzioni effettuano chiamate nel modello a oggetti dell'applicazione host usando le informazioni sul tipo di assembly di interoperabilità primario incorporato nell'assembly della soluzione, anziché chiamare direttamente l'assembly di interoperabilità primario. Per altre informazioni, vedere [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md).

### <a name="loading-process"></a>Processo di caricamento
 Quando un utente avvia un'applicazione, vengono eseguite le operazioni seguenti:

1. L'applicazione cerca nel Registro di sistema le voci che identificano i componenti aggiuntivi VSTO creati mediante gli strumenti di sviluppo per Office in Visual Studio.

2. Se l'applicazione rileva queste voci del Registro di sistema, l'applicazione carica VSTOEE. dll, che carica VSTOLoader. dll. Si tratta di DLL non gestite che sono i componenti del caricatore di Visual Studio 2010 Tools per Office Runtime. Per altre informazioni, vedere panoramica Visual Studio Tools per Office [runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

3. *VSTOLoader.dll* carica e [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] avvia la parte gestita di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

4. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verifica la presenza di aggiornamenti del manifesto e scarica i manifesti della distribuzione e dell'applicazione più recenti.

5. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] esegue una serie di controlli di sicurezza. Per altre informazioni, vedere [Soluzioni Office sicurezza](../vsto/securing-office-solutions.md).

6. Se il componente aggiuntivo VSTO è considerato attendibile per l'esecuzione, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usa i manifesti di distribuzione e dell'applicazione per verificare la disponibilità di aggiornamenti dell'assembly. Se è disponibile una nuova versione dell'assembly, il runtime scarica la nuova versione dell'assembly nella cache di [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] nel computer client. Per altre informazioni, vedere [Deploy an Office solution](../vsto/deploying-an-office-solution.md).

7. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea un nuovo dominio dell'applicazione in cui caricare l'assembly del componente aggiuntivo VSTO.

8. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] carica quindi l'assembly del componente aggiuntivo VSTO nel dominio dell'applicazione.

9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama il metodo <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> nel componente aggiuntivo VSTO, se ne è stato eseguito l'override.

     Facoltativamente, è possibile eseguire l'override di questo metodo per esporre un oggetto nel componente aggiuntivo VSTO ad altre soluzioni Microsoft Office. Per altre informazioni, vedere [Chiamare il codice in VSTO componenti aggiuntivi](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)da altre Office soluzioni .

10. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama il metodo <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> nel componente aggiuntivo VSTO, se ne è stato eseguito l'override.

     È facoltativamente possibile eseguire l'override di questo metodo per estendere una funzionalità di Microsoft Office restituendo un oggetto che implementa un'interfaccia di estensibilità. Per altre informazioni, vedere [Personalizzare le funzionalità dell'interfaccia utente usando le interfacce di estendibilità.](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)

    > [!NOTE]
    > [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] effettua una chiamata a specifica al metodo <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> per ogni interfaccia di estensibilità supportata dall'applicazione host. Anche se la prima chiamata al metodo <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> viene effettuata prima di quella al metodo `ThisAddIn_Startup` , il componente aggiuntivo VSTO non deve formulare ipotesi in merito a quando verrà chiamato il metodo <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> o al numero di volte in cui verrà chiamato.

11. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama il metodo `ThisAddIn_Startup` nel componente aggiuntivo VSTO. Questo metodo è il gestore eventi predefinito per l'evento <xref:Microsoft.Office.Tools.AddInBase.Startup> . Per altre informazioni, vedere [Eventi nei Office .](../vsto/events-in-office-projects.md)

## <a name="see-also"></a>Vedi anche
- [Architettura delle Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)
- [Visual Studio Tools per Office di runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Componenti aggiuntivi VSTO programma](../vsto/programming-vsto-add-ins.md)
- [Sviluppare Office soluzioni](../vsto/developing-office-solutions.md)
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
