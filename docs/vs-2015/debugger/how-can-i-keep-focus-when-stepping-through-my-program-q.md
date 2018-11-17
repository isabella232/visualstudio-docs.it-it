---
title: Come è possibile mantenere lo stato attivo quando si esegue un programma istruzione per istruzione? | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.stepping
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], stepping
- focus, keeping
- stepping, focus
- windows, troubleshooting activation
ms.assetid: 11a30580-3a1a-4be8-a241-0abdc758302e
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 253d331003373138a66fbe1263e6cb71eb126bc0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792437"
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-program"></a>Come è possibile mantenere lo stato attivo quando si esegue un programma istruzione per istruzione?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Descrizione  
 Il programma presenta un problema di attivazione delle finestre. L'esecuzione istruzione per istruzione del programma con il debugger interferisce con la possibilità di riprodurre il problema, poiché il programma non mantiene lo stato attivo. Esiste un metodo per evitare che questo accada?  
  
## <a name="solution"></a>Soluzione  
 Se si dispone di un secondo computer, ricorrere al debug remoto. È possibile eseguire il programma sul computer remoto mentre si esegue il debugger sull'host. Per altre informazioni, vedere [procedura: selezionare un Computer remoto](http://msdn.microsoft.com/en-us/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul codice nativo debug](../debugger/debugging-native-code-faqs.md)   
 [Collegamento a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)



