---
title: Mantenere lo stato attivo quando si esegue un'istruzione alla volta nell'app | Microsoft Docs
description: Usare il debug remoto per evitare che il programma perda lo stato attivo quando si esegue il debug di un problema di attivazione della finestra.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 561e5d4dc009642ee7773cd60d004ef8a64261d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386930"
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-app"></a>Come è possibile mantenere lo stato attivo quando si esegue un'istruzione alla volta nell'app?
## <a name="description"></a>Descrizione
 Il programma presenta un problema di attivazione delle finestre. L'esecuzione istruzione per istruzione del programma con il debugger interferisce con la possibilità di riprodurre il problema, poiché il programma non mantiene lo stato attivo. Esiste un metodo per evitare che questo accada?

## <a name="solution"></a>Soluzione
 Se si dispone di un secondo computer, ricorrere al debug remoto. È possibile eseguire il programma sul computer remoto mentre si esegue il debugger sull'host. Per altre informazioni, [vedere Procedura: Selezionare un computer remoto.](/previous-versions/visualstudio/visual-studio-2010/w8wtw2f3(v=vs.100))

## <a name="see-also"></a>Vedi anche
- [Domande frequenti sul debug di codice nativo](../debugger/debugging-native-code-faqs.md)
- [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)
