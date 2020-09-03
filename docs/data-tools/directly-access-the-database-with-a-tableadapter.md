---
title: Accedere direttamente al database mediante un oggetto TableAdapter
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 22d84e9b4beafd64cc629a295bcfa7f9f67afb6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282566"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Accedere direttamente al database mediante un oggetto TableAdapter

Oltre agli `InsertCommand` oggetti, e, gli `UpdateCommand` `DeleteCommand` oggetti TableAdapter vengono creati con metodi che possono essere eseguiti direttamente sul database. È possibile chiamare questi metodi ( `TableAdapter.Insert` , `TableAdapter.Update` e `TableAdapter.Delete` ) per modificare i dati direttamente nel database.

Se non si desidera creare questi metodi diretti, impostare la proprietà del TableAdapter `GenerateDbDirectMethods` su `false` nella finestra **proprietà** . Se una query viene aggiunta a un TableAdapter oltre alla query principale del TableAdapter, si tratta di query autonome che non generano questi `DbDirect` metodi.

## <a name="send-commands-directly-to-a-database"></a>Inviare comandi direttamente a un database

Chiamare il `DbDirect` metodo TableAdapter che esegue l'attività che si sta tentando di eseguire.

### <a name="to-insert-new-records-directly-into-a-database"></a>Per inserire nuovi record direttamente in un database

- Chiamare il metodo del TableAdapter `Insert` , passando i valori per ogni colonna come parametri. Nella procedura riportata di seguito viene utilizzata `Region` come esempio la tabella nel database Northwind.

    > [!NOTE]
    > Se non si dispone di un'istanza disponibile, creare un'istanza del TableAdapter che si desidera utilizzare.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Per aggiornare i record direttamente in un database

- Chiamare il metodo del TableAdapter `Update` , passando i valori nuovi e originali per ogni colonna come parametri.

    > [!NOTE]
    > Se non si dispone di un'istanza disponibile, creare un'istanza del TableAdapter che si desidera utilizzare.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Per eliminare i record direttamente da un database

- Chiamare il metodo del TableAdapter `Delete` , passando i valori per ogni colonna come parametri del `Delete` metodo. Nella procedura riportata di seguito viene utilizzata `Region` come esempio la tabella nel database Northwind.

    > [!NOTE]
    > Se non si dispone di un'istanza disponibile, creare un'istanza del TableAdapter che si desidera utilizzare.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Vedere anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
