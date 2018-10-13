---
title: 'Estensione Excel di esempio: classe ActionFilter | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: douge
ms.openlocfilehash: 87bffbbd3d463de19c923e6d1bd9f865aca37851
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285395"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Estensione Excel di esempio: classe ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa classe interna estende la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> e rappresenta un filtro per le azioni dei test in un elemento [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
## <a name="simple-properties"></a>Proprietà semplici  
 Queste proprietà di sola lettura consentono allo sviluppatore di specificare come deve essere eseguito il filtro delle azioni dei test dal framework dei test codificati dell'interfaccia utente. Ad esempio, la proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> fornisce il nome del filtro delle azioni. Altre proprietà ottengono il valore <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> del filtro delle azioni, il valore <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, il nome <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> per le azioni di test che vengono filtrate da questo filtro delle azioni di test. Altre indicano se applicare un timeout con <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> e se l'azione di test è <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.  
  
## <a name="processrule-method"></a>Metodo ProcessRule  
 Questo metodo viene chiamato dal framework dei test codificati dell'interfaccia utente ed esegue il filtro sull'oggetto <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> specificato. Questa particolare sostituzione rimuove un'azione scelta dal mouse in una cella quando l'azione successiva nello stack invia sequenze di tasti alla cella. Restituisce quindi `false`.  
  
## <a name="private-methods"></a>Metodi privati  
 Il metodo `IsLeftClick` determina se l'azione fornita rappresenta un clic con il pulsante sinistro del mouse. Il metodo `AreActionsOnSameExcelCell` determina se due azioni fornite vengono eseguite nella stessa cella in Excel.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



