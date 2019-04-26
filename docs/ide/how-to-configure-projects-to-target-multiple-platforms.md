---
title: 'Procedura: Configurare progetti per più piattaforme di destinazione'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5449f0b5cb7d2310f7f71a93236bbe5fd62eacae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824306"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Procedura: Configurare progetti per più piattaforme di destinazione

Visual Studio consente di creare una soluzione per architetture CPU o piattaforme di destinazione diverse. Le proprietà per questa impostazione sono disponibili nella finestra di dialogo **Gestione configurazione**.

## <a name="target-a-platform"></a>Impostare una piattaforma come destinazione

La finestra di dialogo **Gestione configurazione** consente di creare e impostare configurazioni e piattaforme a livello di soluzione e progetto. Ogni combinazione di configurazioni a livello di soluzione e destinazioni può avere un solo set di proprietà associato consentendo di passare facilmente tra una configurazione di versione per una piattaforma [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)], una configurazione di versione per una piattaforma x86 e una configurazione di debug per una piattaforma x86.

1. Nel menu **Compila** fare clic su **Gestione configurazione**.

2. Nella casella **Piattaforma soluzione attiva** selezionare la piattaforma che si vuole impostare come destinazione della soluzione oppure selezionare **\<Nuovo>** per creare una nuova piattaforma. Visual Studio compila l'applicazione impostando come destinazione la piattaforma specificata come piattaforma attiva nella finestra di dialogo **Gestione configurazione**.

## <a name="remove-a-platform"></a>Rimuovere una piattaforma

Se una piattaforma non è più necessaria, è possibile rimuoverla usando la finestra di dialogo **Gestione configurazione**. Verranno rimosse tutte le impostazioni di soluzione e progetto configurate per la combinazione di configurazione e destinazione.

1. Nel menu **Compila** fare clic su **Gestione configurazione**.

2. Nella casella **Piattaforma soluzione attiva** selezionare **\<Modifica>**. Viene visualizzata la finestra di dialogo **Modifica piattaforme soluzione**.

3. Fare clic sulla piattaforma da rimuovere e quindi su **Rimuovi**.

## <a name="target-multiple-platforms-with-one-solution"></a>Impostare più piattaforme come destinazione di un'unica soluzione

Poiché è possibile modificare le impostazioni in base alla combinazione di configurazione e piattaforma, è possibile impostare una soluzione con più piattaforme come destinazione .

### <a name="to-target-multiple-platforms"></a>Per impostare più piattaforme come destinazione

1. Usare **Gestione configurazione** per aggiungere almeno due piattaforme di destinazione per la soluzione.

2. Selezionare la piattaforma di destinazione dall'elenco **Piattaforma soluzione attiva**.

3. Compilare la soluzione.

### <a name="to-build-multiple-solution-configurations-at-once"></a>Per creare più configurazioni di soluzione contemporaneamente

1. Usare **Gestione configurazione** per aggiungere almeno due piattaforme di destinazione per la soluzione.

2. Usare la finestra **Compilazione batch** per compilare più configurazioni di soluzione contemporaneamente.

   È possibile avere una piattaforma a livello di soluzione impostata ad esempio su [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] e non avere all'interno della soluzione alcun progetto per la stessa piattaforma. È anche possibile avere più progetti nella soluzione ognuno con una piattaforma diversa come destinazione. In questi casi è consigliabile creare una nuova configurazione con un nome descrittivo per evitare confusione.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)
- [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)
- [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
