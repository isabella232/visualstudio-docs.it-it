---
title: 'Estensione Excel di esempio: classe ActionFilter | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c286f25159f3ee1934a27d2242e97482f7ec424
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672174"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Estensione Excel di esempio: classe ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa classe interna estende la classe [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) e rappresenta un filtro per le azioni di test su un [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] elemento.

## <a name="simple-properties"></a>Proprietà semplici
 Queste proprietà di sola lettura consentono allo sviluppatore di specificare come deve essere eseguito il filtro delle azioni dei test dal framework dei test codificati dell'interfaccia utente. Ad esempio, la proprietà `UITestActionFilter.Name` fornisce il nome del filtro delle azioni. Altre proprietà ottengono il valore `UITestActionFilter.Category` del filtro delle azioni, il valore `UITestActionFilter.FilterType`, il nome `UITestActionFilter.Group` per le azioni di test che vengono filtrate da questo filtro delle azioni di test. Altre indicano se applicare un timeout con `UITestActionFilter.ApplyTimeout` e se l'azione di test è `UITestActionFilter.Enabled`.

## <a name="processrule-method"></a>Metodo ProcessRule
 Questo metodo viene chiamato dal framework dei test codificati dell'interfaccia utente ed esegue il filtro sull'oggetto `IUITestActionStack` specificato. Questa particolare sostituzione rimuove un'azione scelta dal mouse in una cella quando l'azione successiva nello stack invia sequenze di tasti alla cella. Restituisce quindi `false`.

## <a name="private-methods"></a>Metodi privati
 Il metodo `IsLeftClick` determina se l'azione fornita rappresenta un clic con il pulsante sinistro del mouse. Il metodo `AreActionsOnSameExcelCell` determina se due azioni fornite vengono eseguite nella stessa cella in Excel.

## <a name="see-also"></a>Vedere anche

- [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
