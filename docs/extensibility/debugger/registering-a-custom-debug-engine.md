---
title: Registrazione di un motore di debug personalizzato | Microsoft Docs
description: Informazioni sul modo in cui il motore di debug si registra come class factory, seguendo le convenzioni COM e registrandosi con Visual Studio tramite il registro di sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4581411a2601bf598762a7157f9df0e006995230
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961118"
---
# <a name="register-a-custom-debug-engine"></a>Registrare un motore di debug personalizzato
Il motore di debug deve registrarsi come class factory, seguendo le convenzioni COM, oltre a eseguire la registrazione con Visual Studio tramite la sottochiave del registro di sistema di Visual Studio.

> [!NOTE]
> È possibile trovare un esempio di come registrare un motore di debug nell'esempio TextInterpreter, creato nell'esercitazione relativa alla [creazione di un motore di debug con ATL com](/previous-versions/bb147024(v=vs.90)).

## <a name="dll-server-process"></a>Processo server DLL
 Un motore di debug viene in genere configurato nella propria DLL come server COM. Di conseguenza, il motore di debug deve registrare il CLSID della relativa class factory con COM prima che Visual Studio possa accedervi. Il motore di debug deve quindi registrarsi con Visual Studio per stabilire le proprietà (altrimenti note come metriche) supportate dal motore di debug. La scelta delle metriche scritte nella sottochiave del registro di sistema di Visual Studio dipende dalle funzionalità supportate dal motore di debug.

 Gli [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) descrivono non solo i percorsi del registro di sistema necessari per registrare un motore di debug; viene inoltre descritta la libreria *dbgmetric. lib* , che contiene numerose funzioni e dichiarazioni utili per gli sviluppatori C++ che semplificano la manipolazione del registro di sistema.

### <a name="example"></a>Esempio
 Nell'esempio seguente, dall'esempio TextInterpreter, viene illustrato come utilizzare la `SetMetric` funzione (da *dbgmetric. lib*) per registrare un motore di debug con Visual Studio. Le metriche passate sono definite anche in *dbgmetric. lib*.

> [!NOTE]
> TextInterpreter è un motore di debug di base. non è configurata e pertanto non esegue la registrazione, ovvero qualsiasi altra funzionalità. Un motore di debug più completo ha un elenco completo di `SetMetric` chiamate o dei rispettivi equivalenti, uno per ogni funzionalità supportata dal motore di debug.

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>Vedi anche
- [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Esercitazione: creazione di un motore di debug con ATL COM](/previous-versions/bb147024(v=vs.90))