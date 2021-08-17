---
title: Debug com e ActiveX | Microsoft Docs
description: Suggerimenti sul debug di applicazioni COM e ActiveX controlli in Visual Studio. Informazioni sul debug di server e contenitori COM. Trovare gli strumenti di debug COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- COM, debugging
- debugging ActiveX applications
- debugging [Visual Studio], COM
- debugging COM containers
- ActiveX controls, debugging
ms.assetid: 3260b2a7-3239-493d-9271-aedf705c13c7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5b306be70b9aa75c2f00a88882126fe46712b70679001453d8c6876a0c9965d0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345933"
---
# <a name="com-and-activex-debugging"></a>Debug di COM e ActiveX
In questa sezione vengono forniti suggerimenti sul debug di applicazioni COM e di controlli ActiveX.

## <a name="in-this-section"></a>Contenuto della sezione
 [Debug di server e contenitori COM](../debugger/com-server-and-container-debugging.md) Vengono menzionate considerazioni speciali durante il debug di applicazioni COM. I problemi includono: debug di un server e di un contenitore COM tramite due progetti all'interno della stessa soluzione, traccia di chiamate che attraversano i limiti dei processi, impostazione di punti di interruzione in funzioni di callback ed esecuzione delle istruzioni attraverso e all'interno di contenitori e server.

 [Procedura: Eseguire il debug di un controllo ActiveX controllo](../debugger/how-to-debug-an-activex-control.md) Contiene informazioni sul debug ActiveX controlli. quali: specifica di un contenitore relativo alla sessione di debug per visualizzare come viene eseguito il codice nel controllo ActiveX, debug di un controllo ActiveX con associazione a dati, simulazione di un particolare contenitore ed esecuzione passo passo del codice del contenitore.

 [Strumenti di debug COM](../debugger/com-debugging-tools.md) Elenca i visualizzatori e le applicazioni di esempio che possono essere utili per il debug dell'applicazione COM.

## <a name="related-sections"></a>Sezioni correlate
 [Per prima cosa, esaminare il debugger](../debugger/debugger-feature-tour.md) Vengono forniti collegamenti alle sezioni più grandi della documentazione di debug. Le informazioni includono: novità del debugger, impostazioni e preparazione, punti di interruzione, gestione delle eccezioni, modifica e continuazione, debug di codice gestito, debug di progetti C++, debug di COM e ActiveX, debug di DLL, SQL di debug e riferimenti all'interfaccia utente.

## <a name="see-also"></a>Vedi anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Introduzione a COM](/cpp/atl/introduction-to-com)
- [ActiveX Controlli](/cpp/mfc/activex-controls)
- [Applicazioni server SDI](com-server-and-container-debugging.md)