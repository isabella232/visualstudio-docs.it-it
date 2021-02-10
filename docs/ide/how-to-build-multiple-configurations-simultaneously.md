---
title: 'Procedura: compilare più configurazioni'
description: Informazioni su come creare la maggior parte dei tipi di progetti con più o addirittura tutte le configurazioni di compilazione con un'unica azione IDE.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cabaf226742d867e9d5eccbaf391b723cfbed5d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967670"
---
# <a name="how-to-build-multiple-configurations-in-a-single-build-request"></a>Procedura: compilare più configurazioni in una singola richiesta di compilazione

È possibile compilare la maggior parte dei tipi di progetti con più o addirittura tutte le configurazioni di compilazione con una sola azione IDE usando la finestra di dialogo **compilazione batch** . Tuttavia, non è possibile compilare i seguenti tipi di progetti in più configurazioni della build contemporaneamente:

1. App di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] compilata per Windows usando JavaScript.

2. Tutti i progetti di Visual Basic

3. Progetti CMake.

Se una soluzione contiene un progetto di questi due tipi di progetto, la **compilazione batch** non è disponibile per tale soluzione. In tal caso, il comando non viene visualizzato nel menu **Compila** .

   Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Per compilare un progetto in più configurazioni della build

1. Sulla barra dei menu scegliere **Compila** compilazione  >  **batch**. In alternativa, premere **CTRL** + **Q** per aprire la casella di ricerca e cercare `Batch Build` .

2. Nella colonna **Compila** selezionare le caselle di controllo per le configurazioni in cui si vuole compilare un progetto.

    > [!TIP]
    > Per modificare o creare una configurazione della build per una soluzione, scegliere **Compila**  >  **Configuration Manager** sulla barra dei menu per aprire la finestra di dialogo **Configuration Manager** . Dopo aver modificato una configurazione della build per una soluzione, scegliere il pulsante **Ricompila** nella finestra di dialogo **Compilazione batch** per aggiornare tutte le configurazioni della build per i progetti nella soluzione.

3. Scegliere i pulsanti **Compila** o **Ricompila** per compilare il progetto con le configurazioni specificate.

## <a name="see-also"></a>Vedi anche

- [Procedura: creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)
- [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)
- [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)