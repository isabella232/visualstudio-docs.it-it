---
title: Filtrare e ordinare dati in un'applicazione Windows Forms | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 721f859e93b195340dc181a11bf28850d872ab18
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091512"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrare e ordinare i dati in un'applicazione Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per filtrare i dati, impostare il <xref:System.Windows.Forms.BindingSource.Filter%2A> proprietà da un'espressione stringa che restituisce i record desiderati.  
  
 Per ordinare i dati, impostare il <xref:System.Windows.Forms.BindingSource.Sort%2A> proprietà sul nome di colonna si desidera eseguire l'ordinamento; accodare `DESC` per ordinare in ordine decrescente, o aggiungere `ASC` per ordinare in ordine crescente.  
  
> [!NOTE]
>  Se l'applicazione non usa <xref:System.Windows.Forms.BindingSource> componenti, è possibile filtrare e ordinare i dati utilizzando <xref:System.Data.DataView> oggetti. Per altre informazioni, vedere [DataView](http://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b).  
  
## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Per filtrare i dati utilizzando un BindingSource (componente)  
  
- Impostare il <xref:System.Windows.Forms.BindingSource.Filter%2A> proprietà per l'espressione da restituire. Ad esempio, il codice seguente restituisce i clienti con una `CompanyName` che inizia con "B":  
  
     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]  
  
## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Per ordinare i dati utilizzando un BindingSource (componente)  
  
- Impostare il <xref:System.Windows.Forms.BindingSource.Sort%2A> proprietà per la colonna che si desidera eseguire l'ordinamento. Ad esempio, il codice seguente Ordina i clienti sul `CompanyName` colonna in ordine decrescente:  
  
     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
