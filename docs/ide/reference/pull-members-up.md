---
title: Pull di membri
description: Informazioni su come usare il menu azioni rapide e refactoring per estrarre i membri fino al tipo di base.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 159608644cb641aa2c84e4d55e92156215069030
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616876"
---
# <a name="pull-members-up"></a>Pull di membri

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Consente di eseguire il pull dei membri fino al tipo di base.

**Quando:** È stata implementata un'interfaccia e si desidera spostare un membro nel tipo di base.

**Motivo:** Il pull dei membri consente ad altre implementazioni dell'interfaccia di ereditare anche tali membri.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore in qualsiasi membro di un'interfaccia implementata.
2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

   ![Pull di membri](media/pull-members-up.png)

2. Selezionare **Pull Members up to base type** (Esegui pull di membri al tipo di base).

3. Nella finestra di dialogo selezionare i membri da aggiungere all'interfaccia selezionata.

   ![Eseguire il pull di un membro](media/pull-members-up-dialog.png)

4. Scegliere **OK**. Verrà eseguito il pull dei membri selezionati all'interfaccia.

   ![Pull di membri completato](media/pull-members-up-completed.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
