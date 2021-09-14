---
title: Pull di membri
description: Informazioni su come usare il menu Azioni rapide e refactoring per eseguire il pull dei membri nel tipo di base.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 9abfe9498d1b6bda0c9423566172395d0aca5096
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625859"
---
# <a name="pull-members-up"></a>Pull di membri

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Consente di eseguire il pull dei membri fino al tipo di base.

**Quando:** È stata implementata un'interfaccia e si vuole spostare un membro nel tipo di base.

**Perché:** Il pull dei membri consente anche ad altre implementazioni dell'interfaccia di ereditare tali membri.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore in qualsiasi membro di un'interfaccia implementata.
2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

   ![Pull di membri](media/pull-members-up.png)

2. Selezionare **Pull Members up to base type** (Esegui pull di membri al tipo di base).

3. Nella finestra di dialogo selezionare i membri da aggiungere all'interfaccia selezionata.

   ![Eseguire il pull di un membro](media/pull-members-up-dialog.png)

4. Scegliere **OK**. Verrà eseguito il pull dei membri selezionati all'interfaccia.

   ![Pull di membri completato](media/pull-members-up-completed.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
