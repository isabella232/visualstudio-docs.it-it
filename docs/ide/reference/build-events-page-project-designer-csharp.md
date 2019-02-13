---
title: Pagina Eventi di compilazione, Progettazione progetti (C#)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 49edb08b35b3006901201ccc880a5e74da92f834
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948316"
---
# <a name="build-events-page-project-designer-c"></a>Pagina Eventi di compilazione, Progettazione progetti (C#)
Usare la pagina **Eventi di compilazione** di **Creazione progetti** per specificare le istruzioni di configurazione della build. È anche possibile specificare le condizioni in cui vengono eseguiti gli eventi di post-compilazione. Per altre informazioni, vedere [Procedura: Specificare gli eventi di compilazione (C#)](../../ide/how-to-specify-build-events-csharp.md) e [Procedura: Specificare gli eventi di compilazione (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Elenco UIElement
 **Configurazione** Questo controllo non è modificabile in questa pagina. Per una descrizione di questo controllo, vedere [Pagina Compilazione, Creazione progetti (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Piattaforma**Questo controllo non è modificabile in questa pagina. Per una descrizione di questo controllo, vedere [Pagina Compilazione, Creazione progetti (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Riga di comando dell'evento di pre-compilazione**Specifica i comandi da eseguire prima dell'avvio della compilazione. Per immettere comandi lunghi, fare clic su **Modifica pre-compilazione** per visualizzare la [finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Gli eventi di pre-compilazione non vengono eseguiti se il progetto è aggiornato e non viene attivata alcuna compilazione.


 **Riga di comando dell'evento di post-compilazione**Specifica i comandi da eseguire dopo l'avvio della compilazione. Per immettere comandi lunghi, fare clic su **Modifica post-compilazione** per visualizzare la **finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione**.

> [!NOTE]
> Aggiungere un'istruzione `call` prima di tutti gli eventi di compilazione che eseguono file con estensione BAT. Ad esempio, `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.


 **Eseguire l'evento di post-compilazione**Specifica le condizioni seguenti per l'esecuzione dell'evento di post-compilazione, come illustrato in questa tabella.

|Opzione|Risultato|
|------------|------------|
|**Sempre**|L'evento di post-compilazione verrà sempre eseguito, indipendentemente dall'esito della compilazione.|
|**A compilazione completata**|L'evento di post-compilazione verrà eseguito se la compilazione avrà esito positivo. L'evento verrà quindi eseguito anche per un progetto aggiornato, purché la compilazione abbia esito positivo.|
|**Quando la compilazione aggiorna l'output del progetto**|L'evento di post-compilazione verrà eseguito solo quando il file di output del compilatore (con estensione exe o dll) è diverso dal file di output del compilatore precedente. L'evento di post-compilazione non viene quindi eseguito se un progetto è aggiornato.|

## <a name="see-also"></a>Vedere anche

- [Procedura: Specificare gli eventi di compilazione (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Procedura: Specificare gli eventi di compilazione (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Riferimenti alle proprietà di progetto](../../ide/reference/project-properties-reference.md)
- [Compiling and Building](../../ide/compiling-and-building-in-visual-studio.md) (Compilazione e creazione)