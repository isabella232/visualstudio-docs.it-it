---
title: Supporto dei form nei flussi di lavoro | Microsoft Docs
description: 'Informazioni sul supporto dei moduli nei flussi di lavoro di SharePoint. In un flusso di lavoro possono essere utilizzati quattro tipi di form: associazione, avvio, attività e modifica.'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52939fe00dcbca1cfd633c81d4b0a00ea6b517b9
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915505"
---
# <a name="form-support-in-workflows"></a>Supporto dei form nei flussi di lavoro
  In un flusso di lavoro possono essere utilizzati quattro tipi di form: associazione, avvio, attività e modifica. Questi tipi di form possono essere basati su un form ASPX o un modulo di InfoPath. Il livello di supporto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fornito da per un particolare modulo dipende da diversi fattori, descritti nelle tabelle seguenti. Per ulteriori informazioni sui tipi di form del flusso di lavoro, vedere [Cenni preliminari sui form](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14))dei flussi

## <a name="xml-refactoring"></a>Refactoring XML
 Quando si aggiunge un form di associazione o di avvio di ASPX a un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elemento del progetto del flusso di lavoro, esegue [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automaticamente il refactoring del codice XML nel file di *Elements.xml* del flusso di lavoro per evitare che l'attributo che fa riferimento al form di associazione o di avvio sia sincronizzato quando il nome del modulo o il percorso di distribuzione viene aggiornato o il modulo viene eliminato. Tuttavia, quando si usano altri tipi di form in un flusso di lavoro, ad esempio un'attività o un modulo di modifica, il file di *Elements.xml* non viene sottoposto a refactoring.

## <a name="form-support-in-new-visual-studio-workflows"></a>Supporto dei moduli nei nuovi flussi di lavoro di Visual Studio
 La tabella seguente elenca il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] supporto per diversi tipi di moduli nei moduli ASPX o InfoPath nei flussi di lavoro creati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Tipo di modulo|Flusso di lavoro creato in Visual Studio con un modulo ASPX|Flusso di lavoro creato in Visual Studio tramite un modulo di InfoPath|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Association Rules|-Un form di associazione ASPX può essere aggiunto al flusso di lavoro utilizzando il modello di elemento del **form di associazione del flusso di lavoro** .<br />-Il *Elements.xml* file del flusso di lavoro viene sottoposto a refactoring quando il modulo viene aggiunto, rinominato o eliminato oppure quando viene modificato il percorso di distribuzione.<br />-Per altre informazioni, vedere [procedura dettagliata: creazione di un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Non è presente alcun modello di modulo di associazione InfoPath in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Non esiste alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />-Il file di *Elements.xml* del flusso di lavoro non viene sottoposto a refactoring.|
|Avvio|-Un form di avvio di ASPX può essere aggiunto al flusso di lavoro tramite il modello di elemento del **form di avvio del flusso di lavoro** .<br />-Il *Elements.xml* file del flusso di lavoro viene sottoposto a refactoring quando il modulo viene aggiunto, rinominato o eliminato oppure quando viene modificato il percorso di distribuzione.<br />-Per altre informazioni, vedere [procedura dettagliata: creazione di un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Non è presente alcun modello di modulo di associazione InfoPath in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Non esiste alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />-Il file di *Elements.xml* del flusso di lavoro non viene sottoposto a refactoring.|
|Attività|-Nessun modello di modulo attività ASPX è disponibile in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . È necessario creare una pagina dell'applicazione e aggiungervi codice.<br />-Il file di *Elements.xml* del flusso di lavoro non viene sottoposto a refactoring.<br />-Per altre informazioni, vedere [form attività flusso di lavoro (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14))|-Non è presente alcun modello di modulo attività InfoPath in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Non esiste alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />-Il file di *Elements.xml* del flusso di lavoro non viene sottoposto a refactoring.|
|Modifica|-Nessun modello di modulo di modifica ASPX disponibile in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Per aggiungere un modulo di modifica, è necessario creare una pagina dell'applicazione e aggiungervi codice.<br />-Il file di *Elements.xml* del flusso di lavoro non viene sottoposto a refactoring. È necessario modificarlo manualmente nel modo appropriato.<br />-Per altre informazioni, vedere [form di modifica del flusso di lavoro (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14))|-Non è presente alcun modello di modulo per la modifica di InfoPath in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Non esiste alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />-Il file di *Elements.xml* del flusso di lavoro non viene sottoposto a refactoring.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Supporto dei form nei flussi di lavoro riutilizzabili di SharePoint importati
 La tabella seguente elenca il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] supporto per diversi tipi di moduli nei moduli ASPX o InfoPath nei flussi di lavoro riutilizzabili di SharePoint che vengono importati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Tipo di modulo|Flusso di lavoro riutilizzabile con un form ASPX importato da SharePoint Designer|Flusso di lavoro riutilizzabile con un modulo di InfoPath importato da SharePoint Designer|
|---------------|-------------------------------------------------------------------------------| - |
|Association Rules|-Il form viene usato come riferimento nel file *Elements.xml* del flusso di lavoro.<br />-Il *Elements.xml* file del flusso di lavoro viene sottoposto a refactoring quando il modulo viene rinominato o eliminato oppure quando viene modificato il percorso di distribuzione.|-Il form viene importato, ma non vi viene fatto riferimento nel *Elements.xml* del flusso di lavoro.<br />-Il file di *Elements.xml* del flusso di lavoro non viene sottoposto a refactoring.|
|Avvio|-Al form viene fatto riferimento dal flusso di lavoro nel file *Elements.xml* del flusso di lavoro.<br />-Il *Elements.xml* file del flusso di lavoro viene sottoposto a refactoring quando il modulo viene rinominato o eliminato oppure quando viene modificato il percorso di distribuzione.|-Il form viene importato, ma non vi viene fatto riferimento nel *Elements.xml* del flusso di lavoro.<br />-Il file di *Elements.xml* del flusso di lavoro non viene sottoposto a refactoring. **Nota:**  Per il corretto funzionamento di questo scenario, è necessario aggiungere e modificare le regole e le proprietà.|
|Attività|-Il form viene usato come riferimento nel file *Elements.xml* del flusso di lavoro.<br />-Il file di *Elements.xml* del flusso di lavoro non viene sottoposto a refactoring.|-Il form viene importato, ma non vi viene fatto riferimento nel *Elements.xml* del flusso di lavoro.<br />-Il file di *Elements.xml* del flusso di lavoro non viene sottoposto a refactoring. **Nota:**  Per il corretto funzionamento di questo scenario, è necessario aggiungere e modificare le regole e le proprietà.|
|Modifica|Non applicabile. Impossibile creare moduli di modifica ASPX in SharePoint Designer.|Non applicabile. Non è possibile creare moduli di modifica di InfoPath in SharePoint Designer, ad eccezione del flusso di lavoro predefinito di SharePoint Server, che non è incluso nel file con estensione wsp quando il flusso di lavoro viene esportato.|

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: creare un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Creazione di soluzioni flusso di lavoro SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Importa elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
