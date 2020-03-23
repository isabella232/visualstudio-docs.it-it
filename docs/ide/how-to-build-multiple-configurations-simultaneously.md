---
title: 'Procedura: Compilare più configurazioni contemporaneamente'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33cd217a08f62b4919af6d72017176c110cf5e5a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904087"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Procedura: Compilare più configurazioni contemporaneamente

È possibile compilare la maggior parte dei tipi di progetti con più configurazioni della build o con tutte le configurazioni contemporaneamente usando la finestra di dialogo **Compilazione batch**. Tuttavia, non è possibile compilare i seguenti tipi di progetti in più configurazioni della build contemporaneamente:

1. App di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] compilata per Windows usando JavaScript.

2. Tutti i progetti di Visual Basic

Se una soluzione contiene qualsiasi progetto di questi due tipi di progetto, **la compilazione Batch** non è disponibile per tale soluzione. In tal caso, il comando non viene visualizzato nel menu **Compila.**

   Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Per compilare un progetto in più configurazioni della build

1. Nella barra dei menu scegliere **Compila** > **compilazione batch**. In alternativa, premere **CTRL**+**Q** per aprire `Batch Build`la casella di ricerca e cercare .

2. Nella colonna **Compila** selezionare le caselle di controllo per le configurazioni in cui si vuole compilare un progetto.

    > [!TIP]
    > Per modificare o creare una configurazione di compilazione per una soluzione, scegliere **Gestione configurazione di compilazione** > **Configuration Manager** sulla barra dei menu per aprire la finestra di dialogo **Gestione configurazione.** Dopo aver modificato una configurazione della build per una soluzione, scegliere il pulsante **Ricompila** nella finestra di dialogo **Compilazione batch** per aggiornare tutte le configurazioni della build per i progetti nella soluzione.

3. Scegliere i pulsanti **Compila** o **Ricompila** per compilare il progetto con le configurazioni specificate.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare e modificare configurazioni](../ide/how-to-create-and-edit-configurations.md)
- [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)
- [Compilare più progetti in paralleloBuild multiple projects in parallel](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)