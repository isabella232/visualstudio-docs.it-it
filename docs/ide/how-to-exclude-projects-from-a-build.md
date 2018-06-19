---
title: 'Procedura: escludere progetti da una compilazione'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e203fd9f1515e212591afe11c246cdeb78201b8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949984"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Procedura: escludere progetti da una compilazione

È possibile compilare una soluzione senza compilare tutti i progetti contenuti al suo interno. Ad esempio, si può escludere un progetto che causa l'interruzione della compilazione. Sarà possibile compilare il progetto in seguito, dopo avere esaminato e risolto i problemi.

Per escludere un progetto è possibile procedere in due modi:

-   Rimuoverlo temporaneamente dalla configurazione della soluzione attiva.

-   Creare una configurazione di soluzione che non includa il progetto.

Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Per rimuovere temporaneamente un progetto dalla configurazione della soluzione attiva.

1.  Nella barra dei menu scegliere **Compilazione** > **Gestione configurazione**.

2.  Nella tabella **Contesti progetto** individuare il progetto da escludere dalla compilazione.

3.  Nella colonna **Compilazione** del progetto deselezionare la casella di controllo.

4.  Scegliere il pulsante **Chiudi** e quindi ricompilare la soluzione.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Per creare una configurazione di soluzione che esclude un progetto

1.  Nella barra dei menu scegliere **Compilazione** > **Gestione configurazione**.

2.  Nell'elenco **Configurazione soluzione attiva** **scegliere \<Nuova**.

3.  Nella casella **Nome** immettere un nome per la configurazione della soluzione.

4.  Nell'elenco **Copia impostazioni da** scegliere la configurazione di soluzione su cui si vuole basare la nuova configurazione (ad esempio **Debug**) e quindi scegliere il pulsante **OK**.

5.  Nella finestra di dialogo **Configuration Manager** deselezionare la casella di controllo **Compilazione** per il progetto da escludere e quindi scegliere il pulsante **Chiudi**.

6.  Sulla barra degli strumenti **Standard** verificare che la nuova configurazione della soluzione compaia come configurazione attiva nella casella **Configurazioni soluzione**.

7.  Sulla barra dei menu scegliere **Compila** > **Ricompila soluzione**.

## <a name="see-also"></a>Vedere anche

- [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)
- [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)
- [Procedura: Compilare più configurazioni contemporaneamente](../ide/how-to-build-multiple-configurations-simultaneously.md)