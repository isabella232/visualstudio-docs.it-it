---
title: 'Procedura: Compilare più configurazioni contemporaneamente'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac8d27397c6e4748546e21baf84abd7578ce8762
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547799"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Procedura: Compilare più configurazioni contemporaneamente

È possibile compilare la maggior parte dei tipi di progetti con più configurazioni della build o con tutte le configurazioni contemporaneamente usando la finestra di dialogo **Compilazione batch**. Tuttavia, non è possibile compilare i seguenti tipi di progetti in più configurazioni della build contemporaneamente:

1. App di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] compilata per Windows usando JavaScript.

2. Tutti i progetti di Visual Basic

   Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Per compilare un progetto in più configurazioni della build

1. Nella barra dei menu scegliere **Compilazione** > **Compilazione batch**.

2. Nella colonna **Compila** selezionare le caselle di controllo per le configurazioni in cui si vuole compilare un progetto.

    > [!TIP]
    > Per modificare o creare una configurazione della build per una soluzione, scegliere **Compilazione** > **Gestione configurazione** nella barra dei menu per aprire la finestra di dialogo **Gestione configurazione**. Dopo aver modificato una configurazione della build per una soluzione, scegliere il pulsante **Ricompila** nella finestra di dialogo **Compilazione batch** per aggiornare tutte le configurazioni della build per i progetti nella soluzione.

3. Scegliere i pulsanti **Compila** o **Ricompila** per compilare il progetto con le configurazioni specificate.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)
- [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)
- [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)