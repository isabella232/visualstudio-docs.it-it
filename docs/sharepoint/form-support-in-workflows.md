---
title: Modulo di supporto nei flussi di lavoro | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b3a07f56819818e55548292f3dbcdc1095d9f00
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326080"
---
# <a name="form-support-in-workflows"></a>Supporto dei form nei flussi di lavoro
  Quattro tipi di moduli possono essere utilizzati in un flusso di lavoro: associazione, avvio, attività e la modifica. Questi tipi di form possono basarsi su un form ASPX o un modulo di InfoPath. Il livello di supporto che [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fornisce per un particolare modulo dipende da diversi fattori, che sono descritte nelle tabelle seguenti. Per altre informazioni sui tipi di modulo del flusso di lavoro, vedere [Cenni preliminari sui form del flusso di lavoro](http://go.microsoft.com/fwlink/?LinkId=185228) sul sito Web MSDN.  
  
## <a name="xml-refactoring"></a>Refactoring di XML
 Quando si aggiunge un form di associazione o di avvio di ASPX per un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elemento del progetto flusso di lavoro, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automaticamente effettua il refactoring del codice XML in del flusso di lavoro *Elements* file per mantenere l'attributo che fa riferimento all'associazione o avvio sincronizzato ogni volta che il percorso di distribuzione o nome di modulo viene aggiornato il modulo o viene eliminato. Tuttavia, quando si usano altri tipi di modulo in un flusso di lavoro, ad esempio un modulo di attività o di modifica, la *Elements* file non viene effettuato il refactoring.  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>Supporto dei form nei nuovi flussi di lavoro di Visual Studio
 La tabella seguente elenca [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] supporto per i tipi di modulo diversi nei form ASPX o InfoPath nei flussi di lavoro che vengono creati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo di modulo|Flusso di lavoro creato in Visual Studio con un Form ASPX|Flusso di lavoro creato in Visual Studio usando un modulo di InfoPath|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|Associazione|-Un form di associazione ASPX può essere aggiunto al flusso di lavoro usando il **Form di associazione del flusso di lavoro** modello di elemento.<br />-il *Elements* refactoring del file del flusso di lavoro quando il form viene aggiunto, rinominato o eliminato oppure quando viene modificato il relativo percorso di distribuzione.<br />-Per altre informazioni, vedere [procedura dettagliata: creazione di un flusso di lavoro con form di associazione e avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Non è presente alcun modello di modulo InfoPath associazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Non è prevista alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e progettazione di InfoPath.<br />-il *Elements* file del flusso di lavoro non viene effettuato il refactoring.|  
|Avvio|-Un form di avvio di ASPX può essere aggiunto al flusso di lavoro usando il **Form di avvio del flusso di lavoro** modello di elemento.<br />-il *Elements* refactoring del file del flusso di lavoro quando il form viene aggiunto, rinominato o eliminato oppure quando viene modificato il relativo percorso di distribuzione.<br />-Per altre informazioni, vedere [procedura dettagliata: creazione di un flusso di lavoro con form di associazione e avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Non è presente alcun modello di modulo InfoPath associazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Non è prevista alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e progettazione di InfoPath.<br />-il *Elements* file del flusso di lavoro non viene effettuato il refactoring.|  
|Attività|-Nessun modello di form ASPX attività è disponibile in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. È necessario creare una pagina dell'applicazione e aggiungervi codice.<br />-il *Elements* file del flusso di lavoro non viene effettuato il refactoring.<br />-Per altre informazioni, vedere [moduli delle attività del flusso di lavoro (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-Non è presente alcun modello di modulo InfoPath task in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Non è prevista alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e progettazione di InfoPath.<br />-il *Elements* file del flusso di lavoro non viene effettuato il refactoring.|  
|Modifica|-Nessun modello di modulo di modifica di ASPX è disponibile in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per aggiungere un modulo di modifica, è necessario creare una pagina dell'applicazione e aggiungervi codice.<br />-il *Elements* file del flusso di lavoro non viene effettuato il refactoring. È necessario modificare manualmente come appropriato.<br />-Per altre informazioni, vedere [form di modifica del flusso di lavoro (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-Non è presente alcun modello di modulo InfoPath modifica in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Non è prevista alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e progettazione di InfoPath.<br />-il *Elements* file del flusso di lavoro non viene effettuato il refactoring.|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Supporto dei form nei flussi di lavoro riutilizzabile SharePoint importati
 La tabella seguente elenca [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] supporto per i tipi di modulo diversi nei form ASPX o InfoPath in SharePoint flussi di lavoro riutilizzabili che vengono importati nella [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo di modulo|Flusso di lavoro riutilizzabile che dispone di un form ASPX importato da SharePoint Designer|Flusso di lavoro riutilizzabile che dispone di un modulo di InfoPath importato da SharePoint Designer|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Associazione|-Il modulo fa riferimento il *Elements* file del flusso di lavoro.<br />-il *Elements* refactoring del file del flusso di lavoro quando il form viene rinominato o eliminato oppure quando viene modificato il relativo percorso di distribuzione.|-Il modulo viene importato, ma non viene fatto riferimento nel *Elements* del flusso di lavoro.<br />-il *Elements* file del flusso di lavoro non viene effettuato il refactoring.|  
|Avvio|-Il modulo fa riferimento il flusso di lavoro di *Elements* file del flusso di lavoro.<br />-il *Elements* refactoring del file del flusso di lavoro quando il form viene rinominato o eliminato oppure quando viene modificato il relativo percorso di distribuzione.|-Il modulo viene importato, ma non viene fatto riferimento nel *Elements* del flusso di lavoro.<br />-il *Elements* file del flusso di lavoro non viene effettuato il refactoring. **Nota:** regole e le proprietà devono essere aggiunte e modificate per questo scenario.|  
|Attività|-Il modulo fa riferimento il *Elements* file del flusso di lavoro.<br />-il *Elements* file del flusso di lavoro non viene effettuato il refactoring.|-Il modulo viene importato, ma non viene fatto riferimento nel *Elements* del flusso di lavoro.<br />-il *Elements* file del flusso di lavoro non viene effettuato il refactoring. **Nota:** regole e le proprietà devono essere aggiunte e modificate per questo scenario.|  
|Modifica|Non applicabile. Non è possibile creare form modifica ASPX in SharePoint Designer.|Non applicabile. I moduli di InfoPath modifica non è possibile creare in SharePoint Designer, ad eccezione di flusso di lavoro SharePoint Server incorporato, che non è incluso nel file con estensione wsp quando viene esportato il flusso di lavoro.|  
  
## <a name="see-also"></a>Vedere anche
 [Procedura dettagliata: Creare un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Creare soluzioni di flusso di lavoro di SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importare gli elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  
