---
title: Utilità RegPkg | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b046bd72e6fa44eda5d40faea52bd6e5e294528e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255047"
---
# <a name="regpkg-utility"></a>Utilità RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
>  Il modo migliore per registrare i pacchetti in Visual Studio consiste nell'usare i file con estensione pkgdef. In questo modo per la distribuzione di un'estensione senza la necessità di accedere al Registro di sistema, che è un requisito per la distribuzione di VSIX. I file pkgdef vengono creati tramite il [utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Per ulteriori informazioni sulla distribuzione del pacchetto Visual Studio, vedere [spedizione di estensioni di Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 L'utilità RegPkg.exe registra un pacchetto VSPackage con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e lo prepara per la distribuzione. Questa utilità viene usata in background durante lo sviluppo di VSPackage. Viene eseguito come parte del processo di compilazione in modo che è possibile compilare ed eseguire un pacchetto VSPackage nell'hive sperimentale.  
  
 RegPkg può generare gli script del Registro di sistema in diversi formati. È possibile incorporare questi script nei progetti di distribuzione come file con estensione msi progetti o file di set di strumenti di Windows Installer XML.  
  
 RegPkg.exe trova in genere \< *percorso di installazione di Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg segue questa sintassi:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 Esegue la registrazione con il nome specificato  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] radice.  
  
 /regfile:filename  
 Crea un file con estensione reg anziché l'aggiornamento del Registro di sistema.  Non è utilizzabile con /vrgfile o /rgsfile o /wixfile.  
  
 /rgsfile:filename  
 Crea un file con estensione RGS anziché l'aggiornamento del Registro di sistema.  Non è utilizzabile con /vrgfile o /regfile o /wixfile.  
  
 /vrgfile:filename  
 Crea un file .vrg anziché l'aggiornamento del Registro di sistema.  Non è utilizzabile con /regfile o /rgsfile o /wixfile.  
  
 /rgm  
 Crea un file .rgm oltre al file rgs.  Deve essere combinato con /rgsfile.  
  
 /wixfile:filename  
 Crea un file compatibile con set di strumenti Windows Installer XML anziché l'aggiornamento del Registro di sistema.  Non è utilizzabile con /regfile o /rgsfile o /vrgfile.  
  
 /codebase  
 Forza la registrazione dell'utente con CodeBase anziché come Assembly.  
  
 /assembly  
 Forza la registrazione dell'utente con Assembly anziché CodeBase.  
  
 / annullare la registrazione  
 Annulla la registrazione di questo pacchetto.  Non è possibile usare  
  
 con /regfile o /vrgfile /rgsfile o /wixfile.  
  
## <a name="see-also"></a>Vedere anche  
 [Il rilascio di un prodotto](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Risoluzione dei problemi di registrazione dei pacchetti RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)

