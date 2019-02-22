---
title: Pull di membri
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 65ce1b44063fd6152fc300e32e7dd075fa8afcbf
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335854"
---
# <a name="pull-members-up"></a>Pull di membri

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di eseguire il pull di membri al tipo di base.

**Quando:** è stata implementata un'interfaccia e si vuole spostare un membro al tipo di base.

**Perché:** il pull di membri consente ad altre implementazioni dell'interfaccia di ereditare anche questi membri.

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
