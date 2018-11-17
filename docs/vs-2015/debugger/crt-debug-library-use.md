---
title: Uso della libreria CRT di Debug | Microsoft Docs
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
- c.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6bba5b9c1b9d65c867176ac72c0641fac4cd286
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817646"
---
# <a name="crt-debug-library-use"></a>Utilizzo della libreria di debug CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La libreria di runtime del linguaggio C offre un ampio supporto per il debug. Per usare una delle librerie di debug CRT, è necessario collegarlo con [/debug](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103) e la compilazione con **/MDd**, **/MTd**, oppure **/LDd**.  
  
## <a name="remarks"></a>Note  
 Le definizioni e le macro principali del debug CRT sono disponibili nel file di intestazione CRTDBG.h.  
  
 Le funzioni in librerie di debug CRT sono compilate con le informazioni di debug ([/Z7, /Zd, /Zi, /ZI (formato informazioni di Debug)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)) e senza ottimizzazione. Alcune funzioni contengono asserzioni per la verifica di parametri ricevuti e viene fornito il codice sorgente. Grazie a questo codice sorgente è possibile eseguire passo passo le funzioni CRT per accertarsi che funzionino correttamente e rilevare eventuali parametri o stati di memoria errati. Parte della tecnologia CRT è proprietaria e non fornisce codice sorgente per la gestione delle eccezioni, la virgola mobile e alcune altre routine.  
  
 Quando si implementa Visual C++, è possibile scegliere di installare il codice sorgente della libreria di runtime del linguaggio C sul disco rigido. Se non si installa il codice sorgente, sarà necessario il CD-ROM per eseguire un passaggio alla volta le funzioni CRT.  
  
 Per altre informazioni sulle varie librerie di runtime è possibile usare, vedere [librerie di runtime C](http://msdn.microsoft.com/library/a889fd39-807d-48f2-807f-81492612463f).  
  
## <a name="see-also"></a>Vedere anche  
 [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)   
 [/MD, /MT, /LD (uso della libreria di runtime)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)



