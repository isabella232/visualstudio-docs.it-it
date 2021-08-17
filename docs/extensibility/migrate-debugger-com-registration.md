---
title: Eseguire la migrazione della registrazione della classe COM del debugger a 64 bit| Microsoft Docs
description: Informazioni su come registrare classi COM in msvsmon per le estensioni del debugger senza scrivere in HKEY_CLASSES_ROOT.
ms.custom: SEO-VS-2020
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- greggm
ms.openlocfilehash: cd02fe3e8df0372a2a5503c455c706c0006fcef1d14b1ccacfb1695036646415
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375156"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Eseguire la migrazione della registrazione della classe COM del debugger a 64 bit

Per le estensioni del debugger che registrano classi COM in HKEY_CLASSES_ROOT usando regasm, regsvr32 o scrivendo direttamente nel Registro di sistema e caricate *inmsvsmon.exe* (il debugger remoto), è ora possibile fornire questa registrazione a msvsmon senza dover scrivere in HKEY_CLASSES_ROOT. Ciò influisce sugli analizzatori di espressioni del debugger .NET legacy o sui motori di debug configurati per il caricamento *msvsmon.exe* processo.

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass-def

Per usare questa tecnica, aggiungere un.msvsmon-comclass-def.jsnel file accanto a *msvsmon (InstallDir:* \Common7\IDE\Remote Debugger\x64*).

Di seguito è riportato un esempio di file msvsmon-comclass-def che registra una classe gestita e una classe nativa:

FileName: *MyCompany.MyExample.msvsmon-comclass-def.json*

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
