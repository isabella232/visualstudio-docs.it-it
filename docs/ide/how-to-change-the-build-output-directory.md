---
title: 'Procedura: Modificare la directory di output della compilazione'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e74dfb3c9a5e5ccd4a1e61e15a12991433032e6e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989510"
---
# <a name="how-to-change-the-build-output-directory"></a>Procedura: Modificare la directory di output della compilazione

Il percorso dell'output generato dal progetto può essere specificato a livello di singole configurazioni (per debug e/o rilascio).

> [!NOTE]
> Se si ha un progetto **Installazione**, vedere la nota alla fine di questo articolo.

## <a name="change-the-build-output-directory"></a>Modificare la directory di output della compilazione

1.  Nella barra dei menu scegliere **Progetto** > **\<NomeApp> Proprietà**. In alternativa, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**.

2.  Per i progetti Basic, selezionare la scheda **Compilazione** . Per i progetti C#, selezionare la scheda **Compilazione**. Per un progetto C++ o JavaScript, selezionare la scheda **Generale** .

3.  Nell'elenco a discesa della configurazione nella parte superiore, scegliere la configurazione per cui si vuole modificare il percorso di output (debug, rilascio o tutte).

     Individuare la voce relativa al percorso di output (**Percorso dell'output di compilazione** in Visual Basic **Directory di output** in Visual C++, **Percorso di Output** in JavaScript e C#). Specificare una nuova directory dell'output di compilazione relativa alla directory del progetto.

> [!NOTE]
> In un progetto di installazione, la casella **Nome file di output** modifica solo il percorso del file *Setup.exe* file, non il percorso dei file di progetto. Per altre informazioni, vedere **Compilazione, proprietà di configurazione, finestra di dialogo delle proprietà del progetto di distribuzione**.

## <a name="see-also"></a>Vedere anche

- [Pagina Compilazione, Creazione progetti (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Pagina delle proprietà Generale (Progetto)](/cpp/ide/general-property-page-project)
- [Compilare](../ide/compiling-and-building-in-visual-studio.md)