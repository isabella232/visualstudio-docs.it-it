---
title: 'Procedura: Attivare e disattivare la pluralizzazione (Object Relational Designer)'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6675a136b2bbdc1ef19d90ee19ecf7497053bfe1
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282047"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Procedura: Attivare e disattivare la pluralizzazione (Object Relational Designer)
Per impostazione predefinita, quando si trascinano oggetti di database con nomi che terminano in s o IES da **Esplora server** o **Esplora database** sugli [strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), i nomi delle classi di entità generate vengono modificati dal plurale al singolare. Questa modifica viene apportata per rappresentare in modo più preciso il fatto che viene eseguito il mapping della classe di entità, di cui è stata creata un'istanza, a un singolo record di dati. Ad esempio, se si aggiunge una `Customers` tabella a **Progettazione relazionale O/R** , viene generata una classe di entità denominata `Customer` perché la classe conterrà i dati per un singolo cliente.

> [!NOTE]
> La pluralizzazione viene attivata per impostazione predefinita solo nella versione in lingua inglese di Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Per attivare e disattivare la pluralizzazione

1. Scegliere **Opzioni** dal menu **Strumenti**.

2. Nella finestra di dialogo **Opzioni** espandere **Strumenti di database**.

    > [!NOTE]
    > Se il nodo **Strumenti di database** non è visibile, selezionare **Mostra tutte le impostazioni**.

3. Fare clic su **Object Relational Designer**.

4. Impostare la **pluralità dei nomi** su **Enabled**  =  **false** per impostare la **finestra di progettazione O/R** in modo che non modifichi i nomi delle classi.

5. Impostare la **pluralità dei nomi** su **Enabled**  =  **true** per applicare regole di pluralità ai nomi di classe degli oggetti aggiunti a **Progettazione relazionale**oggetti.

## <a name="see-also"></a>Vedi anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
