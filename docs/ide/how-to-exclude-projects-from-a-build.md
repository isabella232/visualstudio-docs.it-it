---
title: 'Procedura: escludere progetti da una compilazione'
description: Informazioni su come usare Visual Studio per compilare una soluzione senza compilare tutti i progetti in essa contenuti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b0e164c24770048495d16da852523b3dd50a43a
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136901"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Procedura: escludere progetti da una compilazione

È possibile compilare una soluzione senza compilare tutti i progetti contenuti al suo interno. Ad esempio, si può escludere un progetto che causa l'interruzione della compilazione. Sarà possibile compilare il progetto in seguito, dopo avere esaminato e risolto i problemi.

Per escludere un progetto è possibile procedere in due modi:

- Rimuoverlo temporaneamente dalla configurazione della soluzione attiva.

- Creare una configurazione di soluzione che non includa il progetto.

Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Per rimuovere temporaneamente un progetto dalla configurazione della soluzione attiva.

1. Nella barra dei menu scegliere **Compila**  >  **Configuration Manager**.

2. Nella tabella **Contesti progetto** individuare il progetto da escludere dalla compilazione.

3. Nella colonna **Compilazione** del progetto deselezionare la casella di controllo.

4. Scegliere il pulsante **Chiudi** e quindi ricompilare la soluzione.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Per creare una configurazione di soluzione che esclude un progetto

1. Nella barra dei menu scegliere **Compila**  >  **Configuration Manager**.

2. Nell'elenco **Configurazione soluzione attiva** scegliere **\<New>** .

3. Nella casella **Nome** immettere un nome per la configurazione della soluzione.

4. Nell'elenco **Copia impostazioni da** scegliere la configurazione di soluzione su cui si vuole basare la nuova configurazione (ad esempio **Debug**) e quindi scegliere il pulsante **OK**.

5. Nella finestra di dialogo **Configuration Manager** deselezionare la casella di controllo **Compilazione** per il progetto da escludere e quindi scegliere il pulsante **Chiudi**.

6. Sulla barra degli strumenti **Standard** verificare che la nuova configurazione della soluzione compaia come configurazione attiva nella casella **Configurazioni soluzione**.

7. Sulla barra dei menu scegliere **Compila**  >  **Ricompila soluzione**.

## <a name="skipped-projects"></a>Progetti ignorati

I progetti possono essere ignorati durante la compilazione perché non sono aggiornati o perché sono esclusi dalla configurazione. Visual Studio USA MSBuild per compilare i progetti. MSBuild compila solo una destinazione se l'output è più vecchio dell'input, come determinato dai timestamp del file. Per forzare una ricompilazione, usare **Build**la  >  **soluzione ricompila**compilazione comando.

Nel riquadro **compilazione** della finestra di **output** , Visual Studio riporta il numero di progetti aggiornati, il numero che è stato compilato correttamente, il numero che ha avuto esito negativo e il numero ignorato. Il conteggio ignorato non include i progetti non compilati perché sono stati aggiornati. Quando i progetti vengono esclusi dalla configurazione attiva, verranno ignorati durante la compilazione. Nell'output di compilazione viene visualizzato un messaggio che indica che il progetto è stato ignorato:

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

Per individuare il motivo per cui un progetto è stato ignorato, prendere nota della configurazione attiva ( `Debug x86` nell'esempio precedente) e scegliere **Compila**  >  **Configuration Manager**. È possibile visualizzare o modificare i progetti che vengono ignorati per ogni configurazione, come descritto in questo articolo.

## <a name="see-also"></a>Vedere anche

- [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)
- [Procedura: creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)
- [Procedura: compilare più configurazioni contemporaneamente](../ide/how-to-build-multiple-configurations-simultaneously.md)
