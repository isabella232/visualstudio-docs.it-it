---
title: Accedere direttamente al database mediante un oggetto TableAdapter
description: Accedere direttamente a un database con un oggetto TableAdapter usando metodi come Insert, Update e Delete per modificare i dati direttamente nel database.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f676e64dc8f79afb6ff9256b0f85d19054f4a00594a5d8fd420e543b048a6e6f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121264610"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Accedere direttamente al database mediante un oggetto TableAdapter

Oltre ai tableadapter , e , vengono creati con metodi che possono `InsertCommand` `UpdateCommand` essere `DeleteCommand` eseguiti direttamente sul database. È possibile chiamare questi metodi ( `TableAdapter.Insert` , e ) per modificare i dati direttamente nel `TableAdapter.Update` `TableAdapter.Delete` database.

Se non si vogliono creare questi metodi diretti, impostare la proprietà del TableAdapter `GenerateDbDirectMethods` su `false` nella **finestra** Proprietà. Se vengono aggiunte query a un oggetto TableAdapter oltre alla query principale del TableAdapter, si tratta di query autonome che non generano questi `DbDirect` metodi.

## <a name="send-commands-directly-to-a-database"></a>Inviare comandi direttamente a un database

Chiamare il metodo TableAdapter `DbDirect` che esegue l'attività che si sta tentando di eseguire.

### <a name="to-insert-new-records-directly-into-a-database"></a>Per inserire nuovi record direttamente in un database

- Chiamare il metodo del `Insert` TableAdapter, passando i valori per ogni colonna come parametri. La procedura seguente usa `Region` la tabella nel database Northwind come esempio.

    > [!NOTE]
    > Se non è disponibile un'istanza di , creare un'istanza del TableAdapter che si vuole usare.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

### <a name="to-update-records-directly-in-a-database"></a>Per aggiornare i record direttamente in un database

- Chiamare il metodo del `Update` TableAdapter, passando i valori nuovi e originali per ogni colonna come parametri.

    > [!NOTE]
    > Se non è disponibile un'istanza di , creare un'istanza del TableAdapter che si vuole usare.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet18":::

### <a name="to-delete-records-directly-from-a-database"></a>Per eliminare record direttamente da un database

- Chiamare il metodo del `Delete` TableAdapter, passando i valori per ogni colonna come parametri del metodo `Delete` . La procedura seguente usa `Region` la tabella nel database Northwind come esempio.

    > [!NOTE]
    > Se non è disponibile un'istanza di , creare un'istanza del TableAdapter che si vuole usare.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet21":::

## <a name="see-also"></a>Vedi anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
