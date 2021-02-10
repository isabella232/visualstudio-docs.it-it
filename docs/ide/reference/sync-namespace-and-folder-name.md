---
title: Spazio dei nomi di sincronizzazione e nome della cartella
description: Informazioni su come usare il menu azioni rapide e refactoring per sincronizzare lo spazio dei nomi e il nome della cartella.
ms.custom: SEO-VS-2020
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e4f10f3555f4edcec031cd4c144bf5a28e9c055d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967150"
---
# <a name="sync-namespace-and-folder-name"></a>Spazio dei nomi di sincronizzazione e nome della cartella

Questo refactoring si applica a:

- C#

**Cosa:** Nome della cartella e dello spazio dei nomi di sincronizzazione.

**Quando:** Si vuole riprogettare le parti della soluzione trascinando un file in una nuova cartella. 

**Motivo:** Si desidera assicurarsi che lo spazio dei nomi sia sempre aggiornato con la nuova struttura di cartelle.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nel nome dello spazio dei nomi.
2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Modifica spazio dei \<folder name> nomi in**.

   ![Sincronizzare lo spazio dei nomi con il nome della cartella](media/sync-namespace-and-folder-name.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
