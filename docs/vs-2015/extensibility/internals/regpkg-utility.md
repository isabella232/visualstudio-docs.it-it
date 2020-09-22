---
title: Utilità RegPkg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1895d3b57e5109f824728021cb1d64f0c527384b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839963"
---
# <a name="regpkg-utility"></a>Utilità RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Il modo migliore per registrare i pacchetti in Visual Studio consiste nell'usare i file con estensione pkgdef. Questo consente la distribuzione dell'estensione senza dover accedere al registro di sistema, che è un requisito per la distribuzione VSIX. I file pkgdef vengono creati usando l' [utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Per altre informazioni sulla distribuzione dei pacchetti di Visual Studio, vedere [spedizione delle estensioni di Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 L'utilità RegPkg.exe registra un pacchetto VSPackage con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e lo prepara per la distribuzione. Questa utilità viene utilizzata dietro le quinte durante lo sviluppo di VSPackage. Viene eseguito come parte del processo di compilazione in modo che sia possibile compilare ed eseguire un pacchetto VSPackage nell'hive sperimentale.  
  
 RegPkg è in grado di generare script del registro di sistema in diversi formati. È possibile incorporare questi script nei progetti di distribuzione, ad esempio i progetti MSI o i file del set di strumenti XML Windows Installer.  
  
 RegPkg.exe si trova in genere in \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg segue questa sintassi:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root: radice  
 Esegue la registrazione nell'oggetto specificato  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] radice.  
  
 /regfile: nomefile  
 Crea un file con estensione reg anziché aggiornare il registro di sistema.  Non può essere usato con/vrgfile o/rgsfile o/wixfile.  
  
 /rgsfile: nomefile  
 Crea un file con estensione rgs anziché aggiornare il registro di sistema.  Non può essere usato con/vrgfile o/regfile o/wixfile.  
  
 /vrgfile: nomefile  
 Crea un file con estensione VRG anziché aggiornare il registro di sistema.  Non può essere usato con/regfile o/rgsfile o/wixfile.  
  
 /rgm  
 Consente di creare un file con estensione RGM, oltre al file RGS.  Deve essere combinato con/rgsfile.  
  
 /wixfile: nomefile  
 Crea una Windows Installer file compatibile con il set di strumenti XML anziché aggiornare il registro di sistema.  Non può essere usato con/regfile o/rgsfile o/vrgfile.  
  
 /codebase  
 Forza la registrazione con codebase anziché con assembly.  
  
 /assembly  
 Forza la registrazione con l'assembly anziché con la codebase.  
  
 /Unregister  
 Annulla la registrazione del pacchetto.  Non può essere usato  
  
 con/regfile o/vrgfile o/rgsfile o/wixfile.  
  
## <a name="see-also"></a>Vedere anche  
 [Rilascio di un prodotto](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Risoluzione dei problemi di registrazione dei pacchetti RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
