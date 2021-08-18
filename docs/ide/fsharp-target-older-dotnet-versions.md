---
title: Usare come destinazione versioni precedenti di .NET Framework per F#
description: Informazioni sull'uso di una versione precedente di .NET Framework come destinazione quando si usa F# in Visual Studio.
ms.date: 07/11/2018
ms.topic: troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: 18fbd6ea01af196ccf9428a495229972c982a617
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034461"
---
# <a name="target-older-versions-of-net-f"></a>Usare come destinazione versioni precedenti di .NET (F#)

Se si prova a destinare un progetto F# a .NET Framework 2.0, 3.0 o 3.5 e Visual Studio è installato in Windows 8.1, può essere visualizzato l'errore seguente:

**This project requires the 2.0 F# runtime, but that runtime is not installed** (Questo progetto richiede la versione 2.0 del runtime F#, ma tale runtime non è installato)

È noto che questo errore viene generato se si verificano contemporaneamente le condizioni seguenti:

- Visual Studio è installato in Windows 8.1.

- Prima dell'installazione di Visual Studio non è stata eseguita l'abilitazione di .NET Framework 3.5.

- Il progetto è destinato a .NET Framework 2.0, 3.0 o 3.5.

Quando viene installato, Visual Studio rileva le versioni di .NET Framework installate. Visual Studio installa il runtime F# 2.0 solo se .NET Framework 3.5 è installato e abilitato.

## <a name="resolve-the-error"></a>Risolvere l'errore

Per risolvere l'errore, eseguire una delle operazioni seguenti:

- Scegliere come destinazione una versione più recente di .NET Framework.

- Abilitare .NET Framework 3.5 in Windows 8.1 e quindi installare il runtime F# 2.0 tramite riparazione dell'installazione di Visual Studio. Di seguito è riportata la procedura con cui eseguire questa operazione.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Per abilitare .NET Framework 3.5 in Windows 8.1

1. Nella schermata **iniziale** digitare **Pannello di controllo**.

   Durante la digitazione, sotto l'intestazione **App** viene visualizzata l'icona **Pannello di controllo**.

2. Scegliere l'icona **Pannello di controllo**, quindi l'icona **Programmi** e infine il collegamento **Attiva o disattiva le funzionalità Windows**.

3. Assicurarsi che la casella di controllo **.NET Framework 3.5 (include .NET 2.0 e 3.0)** sia selezionata e quindi scegliere il pulsante **OK**. Non è necessario selezionare le caselle di controllo dei nodi figlio per i componenti facoltativi di .NET Framework.

   .NET Framework 3.5 è abilitato, se non lo era già.

### <a name="to-install-the-f-20-runtime"></a>Per installare il runtime F# 2.0

Seguire la [procedura di riparazione di Visual Studio](../install/repair-visual-studio.md).

## <a name="see-also"></a>Vedi anche

- [Guida a F# (.NET Framework)](/dotnet/fsharp/)
- [F# in Visual Studio](fsharp-visual-studio.md)
