---
title: Debug di un controllo ActiveX con associazione a dati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 45a2f6e022c753b0fe543f2265c7ac1961fd474a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954260"
---
# <a name="debugging-a-data-bound-activex-control"></a>Debug di un controllo ActiveX con associazione a dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si sviluppa un controllo ActiveX che verrà associato a un controllo origine dati, è possibile creare un'applicazione contenitore e utilizzare il contenitore per eseguire il debug del controllo ActiveX.  
  
 È ad esempio possibile creare un'applicazione a finestre MFC e inserire nella finestra di dialogo il controllo con associazione a dati e un controllo origine dati. Questa applicazione MFC può essere utilizzata per effettuare test in fase di esecuzione, nonché come eseguibile del contenitore per il debug del controllo ActiveX con associazione a dati.  
  
## <a name="using-the-test-container"></a>Utilizzo di Test Container  
 Se si desidera un contenitore facilmente modificabile per il supporto di diverse interfacce sul controllo o sul contenitore, utilizzare ActiveX Test Container come eseguibile per la sessione di debug. In ActiveX Test Container scegliere **Opzioni** dal menu **Contenitore** per attivare le diverse interfacce. Per altre informazioni, vedere [test di proprietà ed eventi con Test Container](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917).  
  
 Per eseguire istruzione per istruzione il codice del contenitore durante il debug, utilizzare la versione di debug del contenitore oppure la versione di debug di ActiveX Control Test Container. Per altre informazioni, vedere [esempio TSTCON: Controllo ActiveX Test Container](http://msdn.microsoft.com/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Controlli ActiveX](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)
