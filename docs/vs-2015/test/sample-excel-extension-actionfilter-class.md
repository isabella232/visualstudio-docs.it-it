---
title: 'Estensione Excel di esempio: Classe ActionFilter | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26eb001de3a8fed7c6bb1d9d1a547aa618e745e8
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871612"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Estensione Excel di esempio: Classe ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa classe interna estende la classe [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) e rappresenta un filtro per le azioni di test [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] su un elemento.

## <a name="simple-properties"></a>Proprietà semplici
 Queste proprietà di sola lettura consentono allo sviluppatore di specificare come deve essere eseguito il filtro delle azioni dei test dal framework dei test codificati dell'interfaccia utente. Ad esempio, la proprietà `UITestActionFilter.Name` fornisce il nome del filtro delle azioni. Altre proprietà ottengono il valore `UITestActionFilter.Category` del filtro delle azioni, il valore `UITestActionFilter.FilterType`, il nome `UITestActionFilter.Group` per le azioni di test che vengono filtrate da questo filtro delle azioni di test. Altre indicano se applicare un timeout con `UITestActionFilter.ApplyTimeout` e se l'azione di test è `UITestActionFilter.Enabled`.

## <a name="processrule-method"></a>Metodo ProcessRule
 Questo metodo viene chiamato dal framework dei test codificati dell'interfaccia utente ed esegue il filtro sull'oggetto `IUITestActionStack` specificato. Questa particolare sostituzione rimuove un'azione scelta dal mouse in una cella quando l'azione successiva nello stack invia sequenze di tasti alla cella. Restituisce quindi `false`.

## <a name="private-methods"></a>Metodi privati
 Il metodo `IsLeftClick` determina se l'azione fornita rappresenta un clic con il pulsante sinistro del mouse. Il metodo `AreActionsOnSameExcelCell` determina se due azioni fornite vengono eseguite nella stessa cella in Excel.

## <a name="see-also"></a>Vedere anche

- [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
