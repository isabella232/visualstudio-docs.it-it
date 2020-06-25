---
title: Mantieni lo stato attivo durante l'esecuzione dell'istruzione nell'app | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.stepping
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], stepping
- focus, keeping
- stepping, focus
- windows, troubleshooting activation
ms.assetid: 11a30580-3a1a-4be8-a241-0abdc758302e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d41a1bf5f71624751fc94f4a72f06e6da5c39630
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350381"
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-app"></a>Come è possibile rimanere concentrati quando si esegue l'istruzione nell'app?
## <a name="description"></a>Descrizione
 Il programma presenta un problema di attivazione delle finestre. L'esecuzione istruzione per istruzione del programma con il debugger interferisce con la possibilità di riprodurre il problema, poiché il programma non mantiene lo stato attivo. Esiste un metodo per evitare che questo accada?

## <a name="solution"></a>Soluzione
 Se si dispone di un secondo computer, ricorrere al debug remoto. È possibile eseguire il programma sul computer remoto mentre si esegue il debugger sull'host. Per ulteriori informazioni, vedere [procedura: selezionare un computer remoto](/previous-versions/visualstudio/visual-studio-2010/w8wtw2f3(v=vs.100)).

## <a name="see-also"></a>Vedi anche
- [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)
- [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)