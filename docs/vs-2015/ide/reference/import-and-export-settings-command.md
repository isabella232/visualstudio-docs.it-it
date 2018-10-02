---
title: Importa/Esporta impostazioni (comando) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4a638686bb0ec111bf551cac0b38bb5d50b1774
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519900"
---
# <a name="import-and-export-settings-command"></a>Importa/Esporta impostazioni (comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [importazione / esportazione impostazioni comando](https://docs.microsoft.com/visualstudio/ide/reference/import-and-export-settings-command).  
  
  
Consente di importare, esportare o reimpostare le impostazioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Opzioni  
 /export:`filename`  
 Facoltativo. Esporta le impostazioni correnti nel file specificato.  
  
 /import:`filename`  
 Facoltativo. Importa le impostazioni correnti nel file specificato.  
  
 /reset  
 Facoltativo. Reimposta le impostazioni correnti.  
  
## <a name="remarks"></a>Note  
 Se si esegue questo comando senza opzioni viene visualizzata l'**Importazione/Esportazione guidata delle impostazioni**. Per altre informazioni, vedere [Procedura: Condividere le impostazioni tra computer o versioni di Visual Studio](http://msdn.microsoft.com/en-us/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Esempio  
 Il comando seguente esporta le impostazioni correnti nel file `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)



