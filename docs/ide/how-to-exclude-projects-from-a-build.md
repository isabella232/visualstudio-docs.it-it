---
title: 'Procedura: escludere progetti da una compilazione'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a19c49482c45aa0a3cf5d7cb33eb106adb65b83b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114810"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Procedura: escludere progetti da una compilazione

È possibile compilare una soluzione senza compilare tutti i progetti contenuti al suo interno. Ad esempio, si può escludere un progetto che causa l'interruzione della compilazione. Sarà possibile compilare il progetto in seguito, dopo avere esaminato e risolto i problemi.

Per escludere un progetto è possibile procedere in due modi:

- Rimuoverlo temporaneamente dalla configurazione della soluzione attiva.

- Creare una configurazione di soluzione che non includa il progetto.

Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Per rimuovere temporaneamente un progetto dalla configurazione della soluzione attiva.

1. Nella barra dei menu scegliere **Gestione configurazione compilazione** > **Configuration Manager**.

2. Nella tabella **Contesti progetto** individuare il progetto da escludere dalla compilazione.

3. Nella colonna **Compilazione** del progetto deselezionare la casella di controllo.

4. Scegliere il pulsante **Chiudi** e quindi ricompilare la soluzione.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Per creare una configurazione di soluzione che esclude un progetto

1. Nella barra dei menu scegliere **Gestione configurazione compilazione** > **Configuration Manager**.

2. Nell'elenco **Configurazione soluzione attiva**** scegliere \<Nuova**.

3. Nella casella **Nome** immettere un nome per la configurazione della soluzione.

4. Nell'elenco **Copia impostazioni da** scegliere la configurazione di soluzione su cui si vuole basare la nuova configurazione (ad esempio **Debug**) e quindi scegliere il pulsante **OK**.

5. Nella finestra di dialogo **Configuration Manager** deselezionare la casella di controllo **Compilazione** per il progetto da escludere e quindi scegliere il pulsante **Chiudi**.

6. Sulla barra degli strumenti **Standard** verificare che la nuova configurazione della soluzione compaia come configurazione attiva nella casella **Configurazioni soluzione**.

7. Nella barra dei menu scegliere **Compila** > **soluzione di compilazione**.

## <a name="skipped-projects"></a>Progetti ignorati

I progetti possono essere ignorati durante la compilazione perché non sono aggiornati o perché sono esclusi dalla configurazione. Visual Studio usa MSBuild per compilare i progetti. MSBuild compila una destinazione solo se l'output è precedente all'input, come determinato dai timestamp del file. Per forzare una ricompilazione, utilizzare il comando **Compila** > **soluzione di compilazione**.

Nel riquadro **Compila** della finestra **Output,** Visual Studio segnala il numero di progetti aggiornati, il numero che sono stati compilati correttamente, il numero non riuscito e il numero che sono stati ignorati. Il conteggio ignorato non include i progetti che non sono stati compilati perché aggiornati. Quando i progetti vengono esclusi dalla configurazione attiva, vengono ignorati durante la compilazione. Nell'output di compilazione viene visualizzato un messaggio che indica che il progetto viene ignorato:In the build output, you see a message indicating that the project is skipped:

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

Per scoprire il motivo per cui un`Debug x86` progetto è stato ignorato, prendere nota della configurazione attiva (nell'esempio precedente) e scegliere **Gestione configurazione di compilazione** > **Configuration Manager**. È possibile visualizzare o modificare i progetti ignorati per ogni configurazione, come descritto in questo articolo.

## <a name="see-also"></a>Vedere anche

- [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)
- [Procedura: Creare e modificare configurazioni](../ide/how-to-create-and-edit-configurations.md)
- [Procedura: creare più configurazioni contemporaneamenteHow to: Build multiple configurations simultaneously](../ide/how-to-build-multiple-configurations-simultaneously.md)
