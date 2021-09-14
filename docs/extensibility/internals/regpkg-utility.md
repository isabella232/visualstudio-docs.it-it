---
title: Utilità RegPkg | Microsoft Docs
description: Informazioni su come lRegPkg.exe'utilità registra un VSPackage con Visual Studio e lo prepara per la distribuzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ed91788526177392901a6fd8aa03f139f9267827
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709504"
---
# <a name="regpkg-utility"></a>Utilità RegPkg
> [!NOTE]
> Il modo preferito per registrare i pacchetti in Visual Studio è usare i file con estensione pkgdef. Ciò consente la distribuzione delle estensioni senza dover accedere al Registro di sistema, che è un requisito per la distribuzione VSIX. I file Pkgdef vengono creati tramite [l'utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Per altre informazioni sulla distribuzione Visual Studio pacchetto, vedere [Shipping Visual Studio Extensions](../../extensibility/shipping-visual-studio-extensions.md).

 LRegPkg.exe'utilità registra un VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con e lo prepara per la distribuzione. Questa utilità viene usata in background durante lo sviluppo di VSPackage. Viene eseguito come parte del processo di compilazione in modo da poter compilare ed eseguire un VSPackage nell'hive sperimentale.

 RegPkg può generare script del Registro di sistema in diversi formati. È possibile incorporare questi script nei progetti di distribuzione, ad esempio .msi progetti o Windows file del set di strumenti XML del programma di installazione.

 RegPkg.exe si trova in genere \<*Visual Studio SDK installation path*> in\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg segue questa sintassi:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Esegue la registrazione nella radice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] specificata.

 /regfile:FileName Crea un file con estensione reg anziché aggiornare il Registro di sistema.  Non può essere usato con /vrgfile o /rgsfile o /wixfile.

 /rgsfile:FileName Crea un file con estensione rgs anziché aggiornare il Registro di sistema.  Non può essere usato con /vrgfile o /regfile o /wixfile.

 /vrgfile:FileName Crea un file con estensione vrg anziché aggiornare il Registro di sistema.  Non può essere usato con /regfile o /rgsfile o /wixfile.

 /rgm Crea un file con estensione rgm oltre al file rgs.  Deve essere combinato con /rgsfile.

 /wixfile:FileName Crea un file Windows file compatibile con il set di strumenti XML del programma di installazione anziché aggiornare il Registro di sistema.  Non può essere usato con /regfile o /rgsfile o /vrgfile.

 /codebase Forza la registrazione con CodeBase anziché con Assembly.

 /assembly Forza la registrazione con Assembly anziché con CodeBase.

 /unregister Annulla la registrazione del pacchetto.  Non può essere usato

 con /regfile o /vrgfile o /rgsfile o /wixfile.

## <a name="see-also"></a>Vedi anche
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Risoluzione dei problemi di registrazione dei pacchetti RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
