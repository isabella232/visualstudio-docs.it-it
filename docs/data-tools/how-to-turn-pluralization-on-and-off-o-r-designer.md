---
title: 'Procedura: attivare la pluralizzazione e disattiva (O-R Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a8c477ac276ce0ff9c292dc42ba2f5f7d1e53dd9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921683"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Procedura: attivare e disattivare (O/R Designer) la pluralizzazione
Per impostazione predefinita, quando si trascinano oggetti di database con nomi che terminano in s o ies da **Esplora Server**/**Esplora Database** sul [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), vengono modificati i nomi delle classi di entità generate dal plurale al singolare. Questa modifica viene apportata per rappresentare in modo più preciso il fatto che viene eseguito il mapping della classe di entità, di cui è stata creata un'istanza, a un singolo record di dati. Ad esempio, l'aggiunta di una tabella Customers a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] determina una classe di entità denominata Customer poiché conterrà dati relativi a un solo cliente.

> [!NOTE]
>  La pluralizzazione viene attivata per impostazione predefinita solo nella versione in lingua inglese di Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Per attivare e disattivare la pluralizzazione

1.  Scegliere **Opzioni** dal menu **Strumenti**.

2.  Nel **opzioni** finestra di dialogo espandere **Database Tools**.

    > [!NOTE]
    >  Selezionare **Mostra tutte le impostazioni** se il **Database Tools** nodo non è visibile.

3.  Fare clic su **O/R Designer**.

4.  Impostare **pluralizzazione di nomi** a **abilitato** = **False** per impostare il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] in modo che non modifica i nomi delle classi.

5.  Impostare **pluralizzazione di nomi** a **abilitato** = **True** per applicare le regole di pluralizzazione ai nomi di classe di oggetti aggiunti al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)