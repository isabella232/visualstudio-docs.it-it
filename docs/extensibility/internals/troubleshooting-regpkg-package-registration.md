---
title: Risoluzione dei problemi relativi alla registrazione del pacchetto RegPkg | Microsoft Docs
description: Usare queste informazioni per risolvere i problemi di registrazione del pacchetto RegPkg in Visual Studio. Usare la versione di RegPkg appropriata per il pacchetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fbefcdd5bbb0193339fab1b91335e16fcc0e820afd97ad35a7d39ee71582ff06
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431760"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Risoluzione dei problemi di registrazione dei pacchetti RegPkg
> [!NOTE]
> Il modo migliore per registrare i pacchetti in Visual Studio è usare i file con estensione pkgdef. Ciò consente la distribuzione delle estensioni senza dover accedere al Registro di sistema. I file Pkgdef vengono creati tramite [l'utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Per registrare un pacchetto usando RegPkg in , è necessario usare la versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] RegPkg appropriata per il pacchetto.

## <a name="regpkg-versions-related-to-package-versions"></a>Versioni di RegPkg correlate alle versioni del pacchetto
 Esistono due versioni di RegPkg. Una versione è inclusa in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Usare questa versione per registrare i pacchetti compilati usando uno degli assembly seguenti:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Non è possibile registrare i pacchetti compilati usando l'assembly Microsoft.VisualStudio.Shell.dll precedente.

   La versione precedente di RegPkg può registrare i pacchetti compilati usando l'Microsoft.VisualStudio.Shell.dll assembly. Tuttavia, non può registrare i pacchetti compilati usando versioni successive dell'assembly.

## <a name="see-also"></a>Vedi anche
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Visual Studio risoluzione dei problemi](/troubleshoot/visualstudio/welcome-visual-studio/)
