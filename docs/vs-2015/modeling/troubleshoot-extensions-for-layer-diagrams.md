---
title: Risolvere i problemi relativi alle estensioni per i diagrammi livello | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd4560673259373b68b370e73a43de424fb7bdb7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658480"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Risoluzione dei problemi relativi a estensioni per diagrammi livello
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo argomento risolve alcuni problemi che possono verificarsi quando si creano estensioni del modello di livello.

#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-includevsprvsincludesvsprvs-mdmd"></a>Quando si preme F5 per eseguire il debug dell'estensione, i comandi, i gestori movimenti, le estensioni di convalida o le proprietà personalizzate non vengono visualizzate nei diagrammi livello nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

1. Aprire la soluzione di estensione nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e scegliere **Ricompila soluzione**dal menu **Compila** .

2. Premere **F5** o **CTRL + F5** per avviare l'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Aprire un diagramma livello e testare l'estensione.

   Continuare con la procedura descritta di seguito, se necessario.

#### <a name="an-old-version-of-my-extension-runs"></a>Viene seguita una versione precedente dell'estensione.

1. Assicurarsi che non sia in esecuzione un'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

2. Eliminare la cartella seguente:%LocalAppData%\Microsoft\VisualStudio \\ [Version] \ComponentModelCache

   > [!NOTE]
   > % LocalAppData% è in genere *driveName*: \Users \\*nomeutente*\AppData\Local.

   Continuare con la procedura descritta di seguito, se necessario.

#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Viene visualizzata una versione precedente dei risultati di convalida o il metodo di convalida non viene chiamato.

1. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] scegliere **Pulisci soluzione**dal menu **Compila** . In questo modo vengono cancellati i risultati delle precedenti analisi di convalida memorizzati nella cache.

2. Assicurarsi che i livelli nel modello siano associati a elementi di codice e che nel modello sia presente almeno un collegamento di dipendenza. La convalida non viene richiamata se non sono presenti elementi da convalidare.

3. I punti di interruzione normali potrebbero non funzionare in un metodo di convalida, perché è in esecuzione in un processo distinto. È necessario inserire una chiamata a `System.Diagnostics.Debugger.Launch()` se si vuole eseguire il metodo un'istruzione alla volta.

4. In **source. Extension. vsixmanifest** nel progetto di convalida dei livelli, verificare di aver aggiunto sia un elemento del **componente MEF** sia un elemento del **tipo di estensione personalizzato** in **contenuto**.

## <a name="see-also"></a>Vedere anche
 [Estendere i diagrammi livello](../modeling/extend-layer-diagrams.md)
