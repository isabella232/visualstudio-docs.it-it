---
title: Utilità RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f811eb37da730d63e199a0e378b8a9122143649e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724439"
---
# <a name="regpkg-utility"></a>Utilità RegPkg
> [!NOTE]
> Il modo migliore per registrare i pacchetti in Visual Studio consiste nell'usare i file con estensione pkgdef. Questo consente la distribuzione dell'estensione senza dover accedere al registro di sistema, che è un requisito per la distribuzione VSIX. I file pkgdef vengono creati usando l' [utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Per altre informazioni sulla distribuzione dei pacchetti di Visual Studio, vedere [spedizione delle estensioni di Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 L'utilità RegPkg. exe registra un pacchetto VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e lo prepara per la distribuzione. Questa utilità viene utilizzata dietro le quinte durante lo sviluppo di VSPackage. Viene eseguito come parte del processo di compilazione in modo che sia possibile compilare ed eseguire un pacchetto VSPackage nell'hive sperimentale.

 RegPkg è in grado di generare script del registro di sistema in diversi formati. È possibile incorporare questi script nei progetti di distribuzione, ad esempio i progetti MSI o i file del set di strumenti XML Windows Installer.

 RegPkg. exe si trova in genere in \<*percorso di installazione di Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg segue questa sintassi:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root: la radice esegue la registrazione nel parametro specificato

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] radice.

 /regfile: FileName crea un file con estensione reg anziché aggiornare il registro di sistema.  Non può essere usato con/vrgfile o/rgsfile o/wixfile.

 /rgsfile: FileName crea un file con estensione rgs anziché aggiornare il registro di sistema.  Non può essere usato con/vrgfile o/regfile o/wixfile.

 /vrgfile: FileName crea un file con estensione VRG anziché aggiornare il registro di sistema.  Non può essere usato con/regfile o/rgsfile o/wixfile.

 /RGM crea un file con estensione RGM oltre al file RGS.  Deve essere combinato con/rgsfile.

 /wixfile: FileName crea una Windows Installer file compatibile con il set di strumenti XML anziché aggiornare il registro di sistema.  Non può essere usato con/regfile o/rgsfile o/vrgfile.

 /codebase forza la registrazione con codebase anziché assembly.

 /assembly forza la registrazione con l'assembly anziché con la codebase.

 /Unregister annulla la registrazione del pacchetto.  Non può essere usato

 con/regfile o/vrgfile o/rgsfile o/wixfile.

## <a name="see-also"></a>Vedere anche
- [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)
- [Risoluzione dei problemi di registrazione dei pacchetti RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)