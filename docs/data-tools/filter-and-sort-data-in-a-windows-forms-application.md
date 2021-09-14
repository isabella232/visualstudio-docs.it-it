---
title: Filtrare e ordinare i dati in un'applicazione Windows Forms
description: Filtrare e ordinare i dati in un'Windows Forms. Impostare la proprietà Filter su un'espressione stringa che restituisce i record desiderati.
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0743bea71f972b5f5baa6909300c2ce669fc30a6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631385"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrare e ordinare i dati in un'applicazione Windows Forms

I dati vengono filtrati impostando <xref:System.Windows.Forms.BindingSource.Filter%2A> la proprietà su un'espressione stringa che restituisce i record desiderati.

Per ordinare i dati, impostare la proprietà sul nome della colonna in base al quale si desidera eseguire l'ordinamento, accodare per ordinare in ordine decrescente o aggiungere per ordinare <xref:System.Windows.Forms.BindingSource.Sort%2A> `DESC` in ordine `ASC` crescente.

> [!NOTE]
> Se l'applicazione non usa <xref:System.Windows.Forms.BindingSource> componenti, è possibile filtrare e ordinare i dati usando gli <xref:System.Data.DataView> oggetti . Per altre informazioni, vedere [DataViews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Per filtrare i dati usando un componente BindingSource

- Impostare la <xref:System.Windows.Forms.BindingSource.Filter%2A> proprietà sull'espressione che si vuole restituire. Ad esempio, il codice seguente restituisce i clienti con un `CompanyName` che inizia con "B":

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet6":::

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Per ordinare i dati usando un componente BindingSource

- Impostare la <xref:System.Windows.Forms.BindingSource.Sort%2A> proprietà sulla colonna in base alla quale si vuole eseguire l'ordinamento. Ad esempio, il codice seguente ordina i clienti in base `CompanyName` alla colonna in ordine decrescente:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet7":::

## <a name="see-also"></a>Vedi anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
