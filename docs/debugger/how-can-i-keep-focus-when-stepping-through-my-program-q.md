---
title: Mantenere lo stato attivo quando la mia app | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1260e82067a201f836f25b213773dfed0f8d8e72
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944350"
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-app"></a>Come è possibile mantenere lo stato attivo quando la mia App?
## <a name="description"></a>Description  
 Il programma presenta un problema di attivazione delle finestre. L'esecuzione istruzione per istruzione del programma con il debugger interferisce con la possibilità di riprodurre il problema, poiché il programma non mantiene lo stato attivo. Esiste un metodo per evitare che questo accada?  
  
## <a name="solution"></a>Soluzione  
 Se si dispone di un secondo computer, ricorrere al debug remoto. È possibile eseguire il programma sul computer remoto mentre si esegue il debugger sull'host. Per altre informazioni, vedere [Procedura: Selezionare un computer remoto](/previous-versions/visualstudio/visual-studio-2010/w8wtw2f3(v=vs.100)).  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)