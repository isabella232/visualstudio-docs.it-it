---
title: Supporto dei moduli nei flussi di lavoro | Microsoft Docs
description: 'Informazioni sul supporto dei moduli nei SharePoint di lavoro. In un flusso di lavoro è possibile usare quattro tipi di moduli: associazione, avvio, attività e modifica.'
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c10373f0c04a6c68faff795d08ff0e288ce02836
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106919"
---
# <a name="form-support-in-workflows"></a>Supporto dei moduli nei flussi di lavoro
  In un flusso di lavoro è possibile usare quattro tipi di moduli: associazione, avvio, attività e modifica. Questi tipi di modulo possono essere basati su un modulo ASPX o infopath. Il livello di supporto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fornito per un particolare modulo dipende da diversi fattori, descritti nelle tabelle seguenti. Per altre informazioni sui tipi di form del flusso di lavoro, vedere [Cenni preliminari sui moduli del flusso di lavoro](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14)).

## <a name="xml-refactoring"></a>Refactoring XML
 Quando si aggiunge un form di associazione o di avvio ASPX a un elemento di progetto del flusso di lavoro, esegue automaticamente il refactoring del codice XML nel fileElements.xmldel flusso di lavoro per mantenere sincronizzato l'attributo che fa riferimento al modulo di associazione o di avvio ogni volta che il nome del modulo o il percorso di distribuzione viene aggiornato o il modulo viene [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eliminato.  Tuttavia, quando si usano altri tipi di modulo in un flusso di lavoro, ad esempio un'attività o un *modulo* di modifica, il fileElements.xmlnon viene refactoring.

## <a name="form-support-in-new-visual-studio-workflows"></a>Supporto dei moduli nei nuovi Visual Studio di lavoro
 La tabella seguente elenca il supporto per diversi tipi di modulo nei moduli ASPX o InfoPath nei flussi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] di lavoro creati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Tipo di modulo|Flusso di lavoro creato in Visual Studio con un form ASPX|Flusso di lavoro creato in Visual Studio usando un modulo di InfoPath|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Association Rules|- È possibile aggiungere un modulo di associazione ASPX al flusso di lavoro usando il modello di elemento **Form di associazione** del flusso di lavoro.<br />- Il *Elements.xml* del flusso di lavoro viene refactoring quando il modulo viene aggiunto, rinominato o eliminato o quando cambia il percorso di distribuzione.<br />- Per altre informazioni, vedere [Procedura dettagliata: Creazione di un flusso di lavoro con i](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)form di associazione e di avvio .|- Non esiste alcun modello di modulo di associazione infoPath in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />- Non esiste alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />- Il *Elements.xml* del flusso di lavoro non viene refactoring.|
|Iniziazione|- È possibile aggiungere un modulo di avvio ASPX al flusso di lavoro usando il modello di elemento **Form** di avvio del flusso di lavoro.<br />- Il *Elements.xml* del flusso di lavoro viene refactoring quando il modulo viene aggiunto, rinominato o eliminato o quando cambia il percorso di distribuzione.<br />- Per altre informazioni, vedere [Procedura dettagliata: Creazione di un flusso di lavoro con i](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)form di associazione e di avvio .|- Non esiste alcun modello di modulo di associazione infoPath in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />- Non esiste alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />- Il *Elements.xml* del flusso di lavoro non viene refactoring.|
|Attività|- Non è disponibile alcun modello di modulo attività ASPX in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . È necessario creare una pagina dell'applicazione e aggiungervi codice.<br />- Il *Elements.xml* del flusso di lavoro non viene refactoring.<br />- Per altre informazioni, vedere [Form attività flusso di lavoro (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14))|- Non esiste alcun modello di modulo attività infoPath in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />- Non esiste alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />- Il *Elements.xml* del flusso di lavoro non viene refactoring.|
|Modifica|- Nessun modello di modulo di modifica ASPX è disponibile in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Per aggiungere un modulo di modifica, è necessario creare una pagina dell'applicazione e aggiungervi codice.<br />- Il *Elements.xml* del flusso di lavoro non viene refactoring. È necessario modificarlo manualmente in base alle esigenze.<br />- Per altre informazioni, vedere [Moduli di modifica del flusso di lavoro (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14))|- Non esiste alcun modello di modulo di modifica di InfoPath in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />- Non esiste alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />- Il *Elements.xml* del flusso di lavoro non viene refactoring.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Supporto dei moduli nei flussi di SharePoint riutilizzabili
 La tabella seguente elenca il supporto per diversi tipi di modulo nei moduli ASPX o InfoPath SharePoint flussi di lavoro [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] riutilizzabili importati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Tipo di modulo|Flusso di lavoro riutilizzabile con un modulo ASPX importato da SharePoint Designer|Flusso di lavoro riutilizzabile con un modulo di InfoPath importato da SharePoint Designer|
|---------------|-------------------------------------------------------------------------------| - |
|Association Rules|- Viene fatto riferimento al modulo nel file *Elements.xml* del flusso di lavoro.<br />- Il *Elements.xml* del flusso di lavoro viene refactoring quando il modulo viene rinominato o eliminato o quando cambia il percorso di distribuzione.|- Il modulo viene importato, ma non viene fatto riferimento nelElements.xml *del* flusso di lavoro.<br />- Il *Elements.xml* del flusso di lavoro non viene refactoring.|
|Iniziazione|- Il flusso di lavoro fa riferimento al modulo nel file *Elements.xml* del flusso di lavoro.<br />- Il *Elements.xml* del flusso di lavoro viene refactoring quando il modulo viene rinominato o eliminato o quando cambia il percorso di distribuzione.|- Il modulo viene importato, ma non viene fatto riferimento nelElements.xml *del* flusso di lavoro.<br />- Il *Elements.xml* del flusso di lavoro non viene refactoring. **Nota:**  Per il funzionamento di questo scenario, è necessario aggiungere e modificare regole e proprietà.|
|Attività|- Viene fatto riferimento al modulo nel file *Elements.xml* del flusso di lavoro.<br />- Il *Elements.xml* del flusso di lavoro non viene refactoring.|- Il modulo viene importato, ma non viene fatto riferimento nelElements.xml *del* flusso di lavoro.<br />- Il *Elements.xml* del flusso di lavoro non viene refactoring. **Nota:**  Per il funzionamento di questo scenario, è necessario aggiungere e modificare regole e proprietà.|
|Modifica|Non applicabile. I moduli di modifica ASPX non possono essere creati in SharePoint Progettazione.|Non applicabile. I moduli di modifica di InfoPath non possono essere creati in SharePoint Designer, ad eccezione del flusso di lavoro predefinito SharePoint Server, che non è incluso nel file con estensione wsp quando il flusso di lavoro viene esportato.|

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Creare un flusso di lavoro con moduli di associazione e avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Creare soluzioni SharePoint flusso di lavoro](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Importare elementi da un sito SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
