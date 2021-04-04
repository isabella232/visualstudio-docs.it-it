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
ms.openlocfilehash: 045da0ade1ce60e2a8d21c24238c8e2b061e8612
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215825"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrare e ordinare i dati in un'applicazione Windows Forms

Per filtrare i dati, impostare la <xref:System.Windows.Forms.BindingSource.Filter%2A> proprietà su un'espressione stringa che restituisce i record desiderati.

Per ordinare i dati, impostare la <xref:System.Windows.Forms.BindingSource.Sort%2A> proprietà sul nome della colonna in base al quale si desidera eseguire l'ordinamento, accodare `DESC` per eseguire l'ordinamento in ordine decrescente o accodare `ASC` per eseguire l'ordinamento in ordine crescente.

> [!NOTE]
> Se l'applicazione non utilizza i <xref:System.Windows.Forms.BindingSource> componenti di, è possibile filtrare e ordinare i dati utilizzando <xref:System.Data.DataView> gli oggetti. Per altre informazioni, vedere [DataViews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Per filtrare i dati tramite un componente BindingSource

- Impostare la <xref:System.Windows.Forms.BindingSource.Filter%2A> proprietà sull'espressione che si desidera restituire. Il codice seguente, ad esempio, restituisce i clienti con un `CompanyName` che inizia con "B":

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet6":::

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Per ordinare i dati tramite un componente BindingSource

- Impostare la <xref:System.Windows.Forms.BindingSource.Sort%2A> proprietà sulla colonna in cui si desidera eseguire l'ordinamento. Il codice seguente, ad esempio, Ordina i clienti sulla `CompanyName` colonna in ordine decrescente:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet7":::

## <a name="see-also"></a>Vedi anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
