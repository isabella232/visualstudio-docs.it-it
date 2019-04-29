---
title: Uso della libreria CRT di Debug | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9434be46f357a97ad01f10ceec184ebe6c52eb43
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565547"
---
# <a name="crt-debug-library-use"></a>Utilizzo della libreria di debug CRT
La libreria di runtime del linguaggio C offre un ampio supporto per il debug. Per usare una delle librerie di debug CRT, è necessario collegarlo con [/debug](/cpp/build/reference/debug-generate-debug-info) e la compilazione con **/MDd**, **/MTd**, oppure **/LDd**.

## <a name="remarks"></a>Note
 Le definizioni e le macro principali del debug CRT sono disponibili nel file di intestazione CRTDBG.h.

 Le funzioni delle librerie di debug CRT sono compilate con informazioni di debug [/Z7, /Zd, /Zi, /ZI (Formato informazioni di debug](/cpp/build/reference/z7-zi-zi-debug-information-format)) e senza ottimizzazione. Alcune funzioni contengono asserzioni per la verifica di parametri ricevuti e viene fornito il codice sorgente. Grazie a questo codice sorgente è possibile eseguire passo passo le funzioni CRT per accertarsi che funzionino correttamente e rilevare eventuali parametri o stati di memoria errati. Parte della tecnologia CRT è proprietaria e non fornisce codice sorgente per la gestione delle eccezioni, la virgola mobile e alcune altre routine.

 Quando si implementa Visual C++, è possibile scegliere di installare il codice sorgente della libreria di runtime del linguaggio C sul disco rigido. Se non si installa il codice sorgente, sarà necessario il CD-ROM per eseguire un passaggio alla volta le funzioni CRT.

 Per ulteriori informazioni sulle varie librerie di runtime che è possibile utilizzare, vedere [Librerie di runtime del linguaggio C](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>Vedere anche

- [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)
- [/MD, /MT, /LD (uso della libreria di runtime)](/cpp/build/reference/md-mt-ld-use-run-time-library)