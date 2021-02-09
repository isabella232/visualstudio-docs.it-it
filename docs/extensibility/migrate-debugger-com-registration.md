---
title: Eseguire la migrazione della registrazione della classe COM del debugger a 64 bit | Microsoft Docs
description: Informazioni su come registrare le classi COM in msvsmon per le estensioni del debugger senza scrivere in HKEY_CLASSES_ROOT.
ms.custom: SEO-VS-2020
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jmartens
ms.workload:
- greggm
ms.openlocfilehash: adc1db57de2167ff3caa0e87e1075c8ff5b462e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886717"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Eseguire la migrazione della registrazione della classe COM del debugger a 64 bit

Per le estensioni del debugger che registrano le classi COM in HKEY_CLASSES_ROOT usando regasm, regsvr32 o scrivendo direttamente nel registro di sistema e caricate in *msvsmon.exe* (debugger remoto), è ora possibile fornire questa registrazione a msvsmon senza dover scrivere in HKEY_CLASSES_ROOT. Questa operazione interessa gli analizzatori di espressioni del debugger .NET legacy o i motori di debug configurati per il caricamento nel processo *msvsmon.exe* .

## <a name="msvsmon-comclass-def"></a>msvsmon-ComClass-def

Per usare questa tecnica, aggiungere un **.msvsmon-comclass-def.jsnel* file accanto a msvsmon (installDir:* \Common7\IDE\Remote Debugger\x64 *).

Di seguito è riportato un esempio di file msvsmon-ComClass-def che registra una classe gestita e una classe nativa:

Nome file: *MyCompany.MyExample.msvsmon-comclass-def.json*

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
