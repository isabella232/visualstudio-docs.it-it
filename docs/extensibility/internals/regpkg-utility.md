---
title: Utilità RegPkg Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cebfd7a9782a2760eb33f7e56bfe16b126fc6251
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705643"
---
# <a name="regpkg-utility"></a>Utilità RegPkg
> [!NOTE]
> Il modo migliore per registrare i pacchetti in Visual Studio consiste nell'utilizzare i file con estensione pkgdef. Ciò consente la distribuzione delle estensioni senza dover accedere al Registro di sistema, che è un requisito per la distribuzione VSIX. I file Pkgdef vengono creati utilizzando [l'utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Per ulteriori informazioni sulla distribuzione del pacchetto di Visual Studio, vedere [Distribuzione delle estensioni](../../extensibility/shipping-visual-studio-extensions.md)di Visual Studio .

 L'utilità RegPkg.exe registra un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pacchetto VSPackage con e lo prepara per la distribuzione. Questa utilità viene utilizzata dietro le quinte durante lo sviluppo di VSPackage.This utility is used behind the scenes during VSPackage development. Viene eseguito come parte del processo di compilazione in modo che è possibile compilare ed eseguire un VSPackage nell'hive sperimentale.

 RegPkg può generare script del Registro di sistema in diversi formati. È possibile incorporare questi script nei progetti di distribuzione, ad esempio progetti con estensione msi o file del set di strumenti XML di Windows Installer.You can incorporate these scripts in deployment projects such as .msi projects or Windows Installer XML Toolset files.

 RegPkg.exe si trova \<in genere nel percorso di installazione di *Visual Studio SDK*>. RegPkg è la seguente sintassi:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Esegue la registrazione nel campo specificato

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] radice.

 /regfile:NomeFile Crea un file reg anziché aggiornare il Registro di sistema.  Non può essere utilizzato con /vrgfile o /rgsfile o /wixfile.

 /rgsfile:NomeFile Crea un file RGS anziché aggiornare il Registro di sistema.  Non può essere utilizzato con /vrgfile o /regfile o /wixfile.

 /vrgfile:NomeFile Crea un file con estensione vrg anziché aggiornare il Registro di sistema.  Non può essere utilizzato con /regfile o /rgsfile o /wixfile.

 /rgm Crea un file RGM oltre al file rgs.  Deve essere combinato con /rgsfile.

 /wixfile:NomeFile Crea un file compatibile con Il set di strumenti XML di Windows Installer anziché aggiornare il Registro di sistema.  Non può essere utilizzato con /regfile o /rgsfile o /vrgfile.

 /codebase Forces registrazione con CodeBase anziché assembly.

 /assembly Forza la registrazione con Assembly anziché CodeBase.

 /unregister Annulla registra questo pacchetto.  Non può essere utilizzato

 con /regfile o /vrgfile o /rgsfile o /wixfile.

## <a name="see-also"></a>Vedere anche
- [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)
- [Risoluzione dei problemi di registrazione dei pacchetti RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
