---
title: 'Procedura: Attivare e disattivare la pluralizzazione (Object Relational Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 769d1760692cad6a6b813ece16d69f4abd3d26b1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402774"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Procedura: Attivare e disattivare la pluralizzazione (Object Relational Designer)
Per impostazione predefinita, quando si trascinano oggetti di database con nomi che terminano in s o ies da **Esplora Server** oppure **Esplora Database** nel [gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), il nomi delle classi di entità generate vengono modificati dal plurale al singolare. Questa modifica viene apportata per rappresentare in modo più preciso il fatto che viene eseguito il mapping della classe di entità, di cui è stata creata un'istanza, a un singolo record di dati. Ad esempio, aggiungendo un `Customers` alla tabella di **O/R Designer** risultante in una classe di entità denominata `Customer` perché la classe conterrà dati per un solo cliente.

> [!NOTE]
> La pluralizzazione viene attivata per impostazione predefinita solo nella versione in lingua inglese di Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Per attivare e disattivare la pluralizzazione

1. Scegliere **Opzioni** dal menu **Strumenti**.

2. Nella finestra di dialogo **Opzioni** espandere **Strumenti di database**.

    > [!NOTE]
    > Se il nodo **Strumenti di database** non è visibile, selezionare **Mostra tutte le impostazioni**.

3. Fare clic su **Object Relational Designer**.

4. Impostare **pluralizzazione di nomi** al **Enabled** = **False** per impostare il **O/R Designer** in modo che non modifica i nomi delle classi .

5. Impostare **pluralizzazione di nomi** al **Enabled** = **True** per applicare le regole di pluralizzazione ai nomi di classe di oggetti aggiunti al **O/R Finestra di progettazione**.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)