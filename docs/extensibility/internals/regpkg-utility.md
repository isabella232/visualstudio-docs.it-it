---
title: Utilità RegPkg | Microsoft Docs
description: Informazioni su come l'utilità RegPkg.exe registra un VSPackage con Visual Studio e lo prepara per la distribuzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ffef522cb85816c36bee1cb623810fb254d1ddec
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2021
ms.locfileid: "111351942"
---
# <a name="regpkg-utility"></a>Utilità RegPkg
> [!NOTE]
> Il modo migliore per registrare i pacchetti in Visual Studio è l'uso di file con estensione pkgdef. Ciò consente la distribuzione dell'estensione senza dover accedere al Registro di sistema, un requisito per la distribuzione VSIX. I file Pkgdef vengono creati tramite [l'utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Per altre informazioni sulla distribuzione Visual Studio pacchetto, vedere [Shipping Visual Studio Extensions.](../../extensibility/shipping-visual-studio-extensions.md)

 LRegPkg.exe utilità registra un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e lo prepara per la distribuzione. Questa utilità viene usata in background durante lo sviluppo di VSPackage. Viene eseguito come parte del processo di compilazione in modo che sia possibile compilare ed eseguire un VSPackage nell'hive sperimentale.

 RegPkg può generare script del Registro di sistema in diversi formati. È possibile incorporare questi script nei progetti di distribuzione, ad esempio .msi progetti o Windows Installer file del set di strumenti XML.

 RegPkg.exe si trova in genere in \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg segue questa sintassi:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Esegue la registrazione nella radice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] specificata.

 /regfile:FileName Crea un file con estensione reg anziché aggiornare il Registro di sistema.  Non può essere usato con /vrgfile o /rgsfile o /wixfile.

 /rgsfile:FileName Crea un file con estensione rgs anziché aggiornare il Registro di sistema.  Non può essere usato con /vrgfile o /regfile o /wixfile.

 /vrgfile:FileName Crea un file con estensione vrg anziché aggiornare il Registro di sistema.  Non può essere usato con /regfile o /rgsfile o /wixfile.

 /rgm Crea un file con estensione rgm oltre al file rgs.  Deve essere combinato con /rgsfile.

 /wixfile:FileName Crea un Windows Installer file compatibile con il set di strumenti XML anziché aggiornare il Registro di sistema.  Non può essere usato con /regfile o /rgsfile o /vrgfile.

 /codebase Forza la registrazione con CodeBase anziché con Assembly.

 /assembly Forza la registrazione con Assembly anziché con CodeBase.

 /unregister Annulla la registrazione del pacchetto.  Non può essere usato

 con /regfile o /vrgfile o /rgsfile o /wixfile.

## <a name="see-also"></a>Vedi anche
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Risoluzione dei problemi di registrazione dei pacchetti RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
