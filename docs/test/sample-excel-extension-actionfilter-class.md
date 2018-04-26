---
title: 'Estensione Excel di esempio: classe ActionFilter'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b15c0bbc76076178bdb541571e11a7599a3c46c2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="sample-excel-extension-actionfilter-class"></a>Estensione Excel di esempio: classe ActionFilter

Questa classe interna estende la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> e rappresenta un filtro per le azioni dei test in un elemento [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

## <a name="simple-properties"></a>Proprietà semplici

Queste proprietà di sola lettura specificano come deve essere eseguito il filtro delle azioni dei test dal framework dei test codificati dell'interfaccia utente. Ad esempio, la proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> fornisce il nome del filtro delle azioni. Altre proprietà ottengono il valore <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> del filtro delle azioni, il valore <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, il nome <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> per le azioni di test che vengono filtrate da questo filtro delle azioni di test. Altre indicano se applicare un timeout con <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> e se l'azione di test è <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.

## <a name="processrule-method"></a>Metodo ProcessRule

Questo metodo viene chiamato dal framework dei test codificati dell'interfaccia utente ed esegue il filtro sull'oggetto <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> specificato. Questa particolare sostituzione rimuove un'azione scelta dal mouse in una cella quando l'azione successiva nello stack invia sequenze di tasti alla cella. Restituisce quindi `false`.

## <a name="private-methods"></a>Metodi privati

Il metodo `IsLeftClick` determina se l'azione fornita rappresenta un clic con il pulsante sinistro del mouse. Il metodo `AreActionsOnSameExcelCell` determina se due azioni fornite vengono eseguite nella stessa cella in Excel.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>
- [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
