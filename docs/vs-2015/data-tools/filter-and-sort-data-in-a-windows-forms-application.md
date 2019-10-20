---
title: Filtrare e ordinare i dati in una Windows Forms Application | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24c623efc141ff84c2585f967596271d1efbc502
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671652"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrare e ordinare i dati in un'applicazione Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per filtrare i dati, impostare la proprietà <xref:System.Windows.Forms.BindingSource.Filter%2A> su un'espressione stringa che restituisce i record desiderati.

 Per ordinare i dati, impostare la proprietà <xref:System.Windows.Forms.BindingSource.Sort%2A> sul nome della colonna su cui si desidera eseguire l'ordinamento. accodare `DESC` per eseguire l'ordinamento in ordine decrescente oppure accodare `ASC` per eseguire l'ordinamento in ordine crescente.

> [!NOTE]
> Se l'applicazione non utilizza <xref:System.Windows.Forms.BindingSource> componenti, è possibile filtrare e ordinare i dati utilizzando <xref:System.Data.DataView> oggetti. Per altre informazioni, vedere [DataViews](https://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Per filtrare i dati tramite un componente BindingSource

- Impostare la proprietà <xref:System.Windows.Forms.BindingSource.Filter%2A> sull'espressione che si desidera restituire. Il codice seguente, ad esempio, restituisce i clienti con un `CompanyName` che inizia con "B":

     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Per ordinare i dati tramite un componente BindingSource

- Impostare la proprietà <xref:System.Windows.Forms.BindingSource.Sort%2A> sulla colonna in cui si desidera eseguire l'ordinamento. Il codice seguente, ad esempio, Ordina i clienti nella colonna `CompanyName` in ordine decrescente:

     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]

## <a name="see-also"></a>Vedere anche
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
