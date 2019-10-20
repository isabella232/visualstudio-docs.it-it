---
title: Accedere direttamente al database con un TableAdapter | Microsoft Docs
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
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 58500e59a624dac55824033b8b9667754a9040c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657366"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Accedere direttamente al database mediante un oggetto TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oltre ai `InsertCommand`, `UpdateCommand` e `DeleteCommand`, gli oggetti TableAdapter vengono creati con metodi che possono essere eseguiti direttamente sul database. È possibile chiamare questi metodi (`TableAdapter.Insert`, `TableAdapter.Update` e `TableAdapter.Delete`) per modificare i dati direttamente nel database.

 Se non si desidera creare questi metodi diretti, impostare la proprietà `GenerateDbDirectMethods` del TableAdapter su `false` nella finestra **Proprietà** . Se una query viene aggiunta a un TableAdapter oltre alla query principale del TableAdapter, si tratta di query autonome che non generano questi metodi DbDirect.

## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly a un database
 Chiamare il metodo TableAdapter DbDirect che esegue l'attività che si sta tentando di eseguire.

#### <a name="to-insert-new-records-directly-into-a-database"></a>Per inserire nuovi record direttamente in un database

- Chiamare il metodo `Insert` del TableAdapter, passando i valori per ogni colonna come parametri. Nella procedura seguente viene utilizzata la tabella `Region` nel database Northwind, ad esempio.

    > [!NOTE]
    > Se non si dispone di un'istanza disponibile, creare un'istanza del TableAdapter che si desidera utilizzare.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

#### <a name="to-update-records-directly-in-a-database"></a>Per aggiornare i record direttamente in un database

- Chiamare il metodo `Update` del TableAdapter, passando i valori nuovi e originali per ogni colonna come parametri.

    > [!NOTE]
    > Se non si dispone di un'istanza disponibile, creare un'istanza del TableAdapter che si desidera utilizzare.

     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]

#### <a name="to-delete-records-directly-from-a-database"></a>Per eliminare i record direttamente da un database

- Chiamare il metodo `Delete` del TableAdapter, passando i valori per ogni colonna come parametri del metodo `Delete`. Nella procedura seguente viene utilizzata la tabella `Region` nel database Northwind, ad esempio.

    > [!NOTE]
    > Se non si dispone di un'istanza disponibile, creare un'istanza del TableAdapter che si desidera utilizzare.

     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]

## <a name="see-also"></a>Vedere anche
 [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
