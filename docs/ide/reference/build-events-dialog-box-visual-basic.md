---
title: Finestra di dialogo Eventi di compilazione (Visual Basic)
description: Informazioni su come usare la finestra di dialogo Eventi di compilazione per specificare le istruzioni di configurazione della compilazione e le condizioni in cui vengono eseguiti gli eventi di pre-compilazione o post-compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- build events, specifying
- pre-build events
- Build Events dialog box
- post-build events
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89526efde0424cecaf8808b0a869e664fec7d2c55d3aa893b9e76c8deec25863
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372634"
---
# <a name="build-events-dialog-box-visual-basic"></a>Finestra di dialogo Eventi di compilazione (Visual Basic)

Usare la finestra di dialogo **Eventi di compilazione** per specificare le istruzioni di configurazione della build. È anche possibile specificare le condizioni in cui vengono eseguiti tutti gli eventi di pre-compilazione o post-compilazione. Per altre informazioni, vedere [Procedura: Specificare gli eventi di compilazione (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

**Riga di comando eventi pre-compilazione**

Specifica i comandi da eseguire prima dell'avvio della compilazione. Per immettere comandi lunghi, fare clic su **Modifica pre-compilazione** per visualizzare la [finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Gli eventi di pre-compilazione non vengono eseguiti se il progetto è aggiornato e non viene attivata alcuna compilazione.

**Riga di comando eventi post-compilazione**

Specifica i comandi da eseguire dopo il completamento della compilazione. Per digitare comandi lunghi, fare clic **su Modifica post-compilazione** per visualizzare la finestra di dialogo Riga di comando eventi **pre-compilazione/post-compilazione.**

> [!NOTE]
> Aggiungere un'istruzione `call` prima di tutti gli eventi di compilazione che eseguono file con estensione BAT. Ad esempio, `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.

**Esegui evento post-compilazione**

Specifica le condizioni per l'evento che la post-compilazione deve eseguire, come illustrato nella tabella seguente.

|Opzione|Risultato|
|------------|------------|
|**Sempre**|L'evento di post-compilazione verrà sempre eseguito, indipendentemente dall'esito della compilazione.|
|**On successful build**|L'evento di post-compilazione verrà eseguito se la compilazione avrà esito positivo. L'evento verrà eseguito anche per un progetto aggiornato, purché la compilazione abbia esito positivo. Si tratta dell'impostazione predefinita.|
|**Quando la compilazione aggiorna l'output del progetto**|L'evento di post-compilazione verrà eseguito solo quando i file di output del compilatore (con estensione exe o dll) saranno diversi dal file di output del compilatore precedente. Un evento di post-compilazione non viene eseguito se un progetto è aggiornato.|

## <a name="see-also"></a>Vedi anche

- [Compilazione (pagina), Creazione progetti (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Procedura: Specificare eventi di compilazione (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)