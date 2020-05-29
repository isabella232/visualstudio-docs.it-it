---
title: 'Procedura: compilare più configurazioni'
ms.date: 05/13/2020
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6d6a3b4f9110f85ff42e8b9dcf6dd531c3802e2
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183548"
---
# <a name="how-to-build-multiple-configurations-in-a-single-build-request"></a>Procedura: compilare più configurazioni in una singola richiesta di compilazione

È possibile compilare la maggior parte dei tipi di progetti con più o addirittura tutte le configurazioni di compilazione con una sola azione IDE usando la finestra di dialogo **compilazione batch** . Tuttavia, non è possibile compilare i seguenti tipi di progetti in più configurazioni della build contemporaneamente:

1. App di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] compilata per Windows usando JavaScript.

2. Tutti i progetti di Visual Basic

3. Progetti CMake.

Se una soluzione contiene un progetto di questi due tipi di progetto, la **compilazione batch** non è disponibile per tale soluzione. In tal caso, il comando non viene visualizzato nel menu **Compila** .

   Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Per compilare un progetto in più configurazioni della build

1. Sulla barra dei menu scegliere **Compila**compilazione  >  **batch**. In alternativa, premere **CTRL** + **Q** per aprire la casella di ricerca e cercare `Batch Build` .

2. Nella colonna **Compila** selezionare le caselle di controllo per le configurazioni in cui si vuole compilare un progetto.

    > [!TIP]
    > Per modificare o creare una configurazione della build per una soluzione, scegliere **Compila**  >  **Configuration Manager** sulla barra dei menu per aprire la finestra di dialogo **Configuration Manager** . Dopo aver modificato una configurazione della build per una soluzione, scegliere il pulsante **Ricompila** nella finestra di dialogo **Compilazione batch** per aggiornare tutte le configurazioni della build per i progetti nella soluzione.

3. Scegliere i pulsanti **Compila** o **Ricompila** per compilare il progetto con le configurazioni specificate.

## <a name="see-also"></a>Vedere anche

- [Procedura: creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)
- [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)
- [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)