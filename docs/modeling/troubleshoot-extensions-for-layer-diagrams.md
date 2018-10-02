---
title: Risolvere i problemi relativi alle estensioni per i diagrammi delle dipendenze
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1ab3e3c2f299adb8a2f0ec5703f81b14fe5fc4ff
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860355"
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Risolvere i problemi relativi alle estensioni per i diagrammi delle dipendenze

Questo argomento risolve alcuni problemi che possono verificarsi quando si creano estensioni del modello di livello.

## <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-visual-studio"></a>Quando si preme F5 per eseguire il debug dell'estensione my, my comandi, i gestori di movimento, estensioni di convalida o le proprietà personalizzate non vengono visualizzate nei diagrammi delle dipendenze nell'istanza sperimentale di Visual Studio

1.  Aprire la soluzione dell'estensione nell'istanza sperimentale di Visual Studio e sui **compilare** menu, fare clic su **Ricompila soluzione**.

2.  Premere **F5** oppure **CTRL+F5** per avviare l'istanza sperimentale di Visual Studio. Aprire un diagramma delle dipendenze e testare l'estensione.

 Continuare con la procedura descritta di seguito, se necessario.

## <a name="an-old-version-of-my-extension-runs"></a>Viene seguita una versione precedente dell'estensione.

1.  Assicurarsi che non sia in esecuzione alcuna istanza sperimentale di Visual Studio.

2.  Eliminare la cartella seguente: %LocalAppData%\Microsoft\VisualStudio\\[versione] \ComponentModelCache

    > [!NOTE]
    > % LocalAppData % corrisponde in genere *DriveName*: \Users\\*UserName*\AppData\Local.

 Continuare con la procedura descritta di seguito, se necessario.

## <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Viene visualizzata una versione precedente dei risultati di convalida o il metodo di convalida non viene chiamato.

1.  Nell'istanza sperimentale di Visual Studio, sul **compilare** menu, fare clic su **Pulisci soluzione**. In questo modo vengono cancellati i risultati delle precedenti analisi di convalida memorizzati nella cache.

2.  Assicurarsi che i livelli nel modello siano associati a elementi di codice e che nel modello sia presente almeno un collegamento di dipendenza. La convalida non viene richiamata se non sono presenti elementi da convalidare.

3.  I punti di interruzione normali potrebbero non funzionare in un metodo di convalida, perché è in esecuzione in un processo distinto. È necessario inserire una chiamata a `System.Diagnostics.Debugger.Launch()` se si vuole eseguire il metodo un'istruzione alla volta.

4.  Nelle **vsixmanifest** nel progetto di convalida dei layer, assicurarsi che sia stato aggiunto un **componente MEF** elemento e un **tipo di estensione personalizzato** elemento sotto **Contenuto**.

## <a name="see-also"></a>Vedere anche

- [Estendere i diagrammi delle dipendenze](../modeling/extend-layer-diagrams.md)
