---
title: 'Procedura: Attivare e disattivare la pluralizzazione (Object Relational Designer)'
description: Informazioni su come attivare e disattivare la pluralizzazione in Object Relational Designer (O/R Designer). L'impostazione predefinita converte i nomi plurali in singolari.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f51d48f2d4af4ed723dbe0dcd720ee460e1feb1b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631296"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Procedura: Attivare e disattivare la pluralizzazione (Object Relational Designer)
Per impostazione predefinita, quando si trascinano oggetti di database con nomi che terminano con s o **ies** da **Esplora server** o Esplora database negli strumenti [LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), i nomi delle classi di entità generate vengono modificati da plurale a singolare. Questa modifica viene apportata per rappresentare in modo più preciso il fatto che viene eseguito il mapping della classe di entità, di cui è stata creata un'istanza, a un singolo record di dati. Ad esempio, l'aggiunta di una tabella a `Customers` **O/R Designer** comporta una classe di entità denominata perché contenerà i dati `Customer` solo per un singolo cliente.

> [!NOTE]
> La pluralizzazione viene attivata per impostazione predefinita solo nella versione in lingua inglese di Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Per attivare e disattivare la pluralizzazione

1. Scegliere **Opzioni** dal menu **Strumenti**.

2. Nella finestra di dialogo **Opzioni** espandere **Strumenti di database**.

    > [!NOTE]
    > Se il nodo **Strumenti di database** non è visibile, selezionare **Mostra tutte le impostazioni**.

3. Fare clic su **Object Relational Designer**.

4. Impostare **Pluralizzazione dei nomi** su **Enabled**  =  **False** per impostare **O/R Designer** in modo che non cambi i nomi delle classi.

5. Impostare **Pluralizzazione dei nomi** su **Enabled** True per applicare le regole di pluralizzazione ai nomi di classe degli oggetti aggiunti a  =   **O/R Designer.**

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
