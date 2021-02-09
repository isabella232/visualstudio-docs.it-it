---
title: Filtrare e ordinare i dati in un'applicazione Windows Forms
description: Filtrare e ordinare i dati in un Windows Forms Application. Impostare la proprietà Filter su un'espressione stringa che restituisce i record desiderati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b1708d6871f1acdf437895563d9b5a39dbe93f21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858852"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrare e ordinare i dati in un'applicazione Windows Forms

Per filtrare i dati, impostare la <xref:System.Windows.Forms.BindingSource.Filter%2A> proprietà su un'espressione stringa che restituisce i record desiderati.

Per ordinare i dati, impostare la <xref:System.Windows.Forms.BindingSource.Sort%2A> proprietà sul nome della colonna in base al quale si desidera eseguire l'ordinamento, accodare `DESC` per eseguire l'ordinamento in ordine decrescente o accodare `ASC` per eseguire l'ordinamento in ordine crescente.

> [!NOTE]
> Se l'applicazione non utilizza i <xref:System.Windows.Forms.BindingSource> componenti di, è possibile filtrare e ordinare i dati utilizzando <xref:System.Data.DataView> gli oggetti. Per altre informazioni, vedere [DataViews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Per filtrare i dati tramite un componente BindingSource

- Impostare la <xref:System.Windows.Forms.BindingSource.Filter%2A> proprietà sull'espressione che si desidera restituire. Il codice seguente, ad esempio, restituisce i clienti con un `CompanyName` che inizia con "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Per ordinare i dati tramite un componente BindingSource

- Impostare la <xref:System.Windows.Forms.BindingSource.Sort%2A> proprietà sulla colonna in cui si desidera eseguire l'ordinamento. Il codice seguente, ad esempio, Ordina i clienti sulla `CompanyName` colonna in ordine decrescente:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Vedi anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
