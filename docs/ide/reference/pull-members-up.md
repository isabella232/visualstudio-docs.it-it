---
title: Pull di membri
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2d1f7deb7aca1fed7b75b66b17ce2e4d63768a0d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969171"
---
# <a name="pull-members-up"></a>Pull di membri

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di eseguire il pull di membri al tipo di base.

**Quando:** è stata implementata un'interfaccia e si vuole spostare un membro al tipo di base.

**Perché?:** il pull di membri consente ad altre implementazioni dell'interfaccia di ereditare anche questi membri.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore in qualsiasi membro di un'interfaccia implementata.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

   ![Pull di membri](media/pull-members-up.png)

2. Selezionare **Pull Members up to base type** (Esegui pull di membri al tipo di base).

3. Nella finestra di dialogo selezionare i membri da aggiungere all'interfaccia selezionata.

   ![Eseguire il pull di un membro](media/pull-members-up-dialog.png)

4. Scegliere **OK**. Verrà eseguito il pull dei membri selezionati all'interfaccia.

   ![Pull di membri completato](media/pull-members-up-completed.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
