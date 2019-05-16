---
title: La registrazione di un oggetto personalizzato di motore di Debug | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cf06e881034b980b8e40e095779007b3c7fa6f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703596"
---
# <a name="registering-a-custom-debug-engine"></a>Registrazione di un motore di debug personalizzato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il motore di debug deve registrarsi come una class factory segue le convenzioni COM, nonché registrare con Visual Studio tramite la sottochiave del Registro di sistema di Visual Studio.  
  
> [!NOTE]
> Un esempio di come registrare un motore di debug è reperibile nell'esempio TextInterpreter, che viene compilato come parte di [esercitazione: Creazione di un motore di Debug tramite ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Processo del Server di DLL  
 In genere, un motore di debug viene implementato la propria DLL come server COM. Ciò significa che il motore di debug è necessario registrare il CLSID della relativa class factory con COM prima di Visual Studio possono accedervi. Quindi il motore di debug deve registrarsi con Visual Studio per poter valutare alcuna proprietà, in caso contrario, noti come le metriche, il debug supporta del motore. La scelta delle metriche che vengono scritti nella sottochiave del Registro di sistema di Visual Studio per il motore di debug dipende dalle funzionalità che supporta il motore di debug.  
  
 [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) descrive non solo le posizioni del Registro di sistema necessarie per registrare un motore di debug; vengono inoltre descritte la libreria dbgmetric.lib, che contiene un numero di funzioni utili e le dichiarazioni per gli sviluppatori C++ che rendono la modifica del Registro di sistema più semplice.  
  
### <a name="example"></a>Esempio  
 Ecco un esempio tipico (dall'esempio TextInterpreter) che illustra come usare il `SetMetric` funzione (da dbgmetric.lib), per registrare un motore di debug con Visual Studio. Le metriche vengono passate sono definite anche nel dbgmetric.lib.  
  
> [!NOTE]
> TextInterpreter è un motore di debug di base; non implementa e pertanto non registra, ovvero qualsiasi altra funzionalità. Un motore di debug più completato potrebbe avere un elenco di `SetMetric` supporta le chiamate o i rispettivi equivalenti, uno per ogni funzionalità motore di debug.  
  
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
 [Creazione di un motore di Debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Helper SDK per eseguire il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Esercitazione: Creazione di un motore di Debug tramite COM ATL](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
