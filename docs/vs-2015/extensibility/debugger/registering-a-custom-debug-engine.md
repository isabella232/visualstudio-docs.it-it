---
title: Registrazione di un motore di debug personalizzato | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703596"
---
# <a name="registering-a-custom-debug-engine"></a>Registrazione di un motore di debug personalizzato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il motore di debug deve registrarsi come class factory le convenzioni COM seguenti, nonché registrarsi in Visual Studio tramite la sottochiave del registro di sistema di Visual Studio.  
  
> [!NOTE]
> Un esempio di come registrare un motore di debug è disponibile nell'esempio TextInterpreter, che viene compilato come parte dell' [esercitazione: creazione di un motore di debug con ATL com](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Processo server DLL  
 In genere, un motore di debug viene implementato nella propria DLL come server COM. Questo significa che il motore di debug deve registrare il CLSID della relativa class factory con COM prima che Visual Studio possa accedervi. Il motore di debug deve quindi registrarsi autonomamente con Visual Studio per stabilire le proprietà (altrimenti note come metriche) supportate dal motore di debug. La scelta delle metriche scritte nella sottochiave del registro di sistema di Visual Studio per il motore di debug dipende dalle funzionalità supportate dal motore di debug.  
  
 Gli [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) descrivono non solo i percorsi del registro di sistema necessari per registrare un motore di debug; viene inoltre descritta la libreria dbgmetric. lib, che contiene numerose funzioni e dichiarazioni utili per gli sviluppatori C++ che semplificano la manipolazione del registro di sistema.  
  
### <a name="example"></a>Esempio  
 Di seguito è riportato un esempio tipico (dall'esempio TextInterpreter) che illustra come usare la `SetMetric` funzione (da dbgmetric. lib) per registrare un motore di debug con Visual Studio. Le metriche passate sono definite anche in dbgmetric. lib.  
  
> [!NOTE]
> TextInterpreter è un motore di debug di base. non implementa, quindi non esegue la registrazione, ovvero qualsiasi altra funzionalità. Un motore di debug più completo ha un elenco completo di `SetMetric` chiamate o dei rispettivi equivalenti, uno per ogni funzionalità supportata dal motore di debug.  
  
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
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Esercitazione: creazione di un motore di debug con ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
