---
title: Registrazione di un motore di debug personalizzato Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe6fb916810bc8a7e960a4723a6a7c7a6f0c1410
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713220"
---
# <a name="register-a-custom-debug-engine"></a>Registrare un motore di debug personalizzatoRegister a custom debug engine
Il motore di debug deve registrarsi come class factory, seguendo le convenzioni COM e con Visual Studio tramite la sottochiave del Registro di sistema di Visual Studio.

> [!NOTE]
> È possibile trovare un esempio di come registrare un motore di debug nell'esempio TextInterpreter, compilato come parte [dell'esercitazione: creazione](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)di un motore di debug utilizzando ATL COM .

## <a name="dll-server-process"></a>Processo server DLL
 Un motore di debug viene in genere impostato nella propria DLL come server COM. Di conseguenza, il motore di debug deve registrare il CLSID della class factory con COM prima che Visual Studio possa accedervi. Quindi, il motore di debug deve registrarsi con Visual Studio per stabilire tutte le proprietà (altrimenti noto come metriche) supportato dal motore di debug. La scelta delle metriche scritte nella sottochiave del Registro di sistema di Visual Studio dipende dalle funzionalità supportate dal motore di debug.

 [Gli helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) descrivono non solo i percorsi del Registro di sistema necessari per registrare un motore di debug; viene inoltre descritta la libreria *dbgmetric.lib,* che contiene una serie di funzioni e dichiarazioni utili per gli sviluppatori di C, che semplificano la modifica del Registro di sistema.

### <a name="example"></a>Esempio
 Nell'esempio seguente (dall'esempio TextInterpreter) `SetMetric` viene illustrato come utilizzare la funzione (da *dbgmetric.lib*), per registrare un motore di debug con Visual Studio. Le metriche passate sono definite anche in *dbgmetric.lib*.

> [!NOTE]
> TextInterpreter è un motore di debug di base; non imposta, e quindi non registra, altre funzioni. Un motore di debug più completo `SetMetric` avrebbe un intero elenco di chiamate o il loro equivalente, uno per ogni funzionalità supportata dal motore di debug.

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

## <a name="see-also"></a>Vedere anche
- [Creazione di un motore di debug personalizzatoCreating a custom debug engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Esercitazione: Compilazione di un motore di debug tramite COM ATLTutorial: Building a debug engine using ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)
