---
title: Registrazione di un motore di debug personalizzato | Microsoft Docs
description: Informazioni su come il motore di debug si registra come class factory, seguendo le convenzioni COM e registrando con Visual Studio tramite il Registro di sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 2499e4aef01bd4812a705afd7777cacd7eb2ba14
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634683"
---
# <a name="register-a-custom-debug-engine"></a>Registrare un motore di debug personalizzato
Il motore di debug deve registrarsi come class factory, seguendo le convenzioni COM e registrarsi con Visual Studio tramite la sottochiave Visual Studio del Registro di sistema.

> [!NOTE]
> È possibile trovare un esempio di come registrare un motore di debug nell'esempio TextInterpreter, compilato come parte dell'esercitazione: Compilazione di un motore di debug tramite [ATL COM.](/previous-versions/bb147024(v=vs.90))

## <a name="dll-server-process"></a>Processo del server DLL
 Un motore di debug viene in genere configurato nella propria DLL come server COM. Di conseguenza, il motore di debug deve registrare il CLSID del class factory con COM prima Visual Studio possibile accedervi. Quindi, il motore di debug deve registrarsi con Visual Studio per stabilire le proprietà (note anche come metriche) supportate dal motore di debug. La scelta delle metriche scritte nella sottochiave Visual Studio del Registro di sistema dipende dalle funzionalità supportate dal motore di debug.

 [Gli helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) descrivono non solo i percorsi del Registro di sistema necessari per registrare un motore di debug. descrive anche la libreria *dbgmetric.lib,* che contiene una serie di funzioni e dichiarazioni utili per gli sviluppatori C++ che semplificano la modifica del Registro di sistema.

### <a name="example"></a>Esempio
 L'esempio seguente (dall'esempio TextInterpreter) illustra come usare la funzione `SetMetric` (da *dbgmetric.lib*), per registrare un motore di debug con Visual Studio. Le metriche passate sono definite anche in *dbgmetric.lib*.

> [!NOTE]
> TextInterpreter è un motore di debug di base. non configura e pertanto non registra altre funzionalità. Un motore di debug più completo avrebbe un intero elenco di chiamate o il relativo equivalente, uno per ogni funzionalità che il motore `SetMetric` di debug supporta.

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
- [Esercitazione: Compilazione di un motore di debug con ATL COM](/previous-versions/bb147024(v=vs.90))