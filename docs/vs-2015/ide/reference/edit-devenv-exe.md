---
title: -Edit (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bbe3adb8967c7571a320bcdf840df6f511c42a7f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242131"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Apre il file specificato in un'istanza esistente di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## <a name="arguments"></a>Argomenti  
 `file1`  
 Facoltativo. File da aprire in un'istanza esistente di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Se non esiste alcuna istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ne viene creata una nuova con un layout di finestra semplificato e `file1` viene aperto nella nuova istanza.  
  
 `file2`  
 Facoltativo. Uno o più file aggiuntivi da aprire nell'istanza esistente di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="remarks"></a>Note  
 Se non è stato specificato alcun file ed è presente un'istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], l'istanza esistente di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] riceve lo stato attivo. Se non è stato specificato alcun file e non è presente un'istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], verrà creata una nuova istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] con un layout di finestra semplificato.  
  
 Se l'istanza esistente di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è in uno stato modale, ad esempio, se la [finestra di dialogo Opzioni](../../ide/reference/options-dialog-box-visual-studio.md) è aperta, il file verrà aperto nell'istanza esistente quando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] esce dallo stato modale.  
  
## <a name="example"></a>Esempio  
 In questo esempio il file `MyFile.cs` viene aperto in un'istanza esistente di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] oppure in una nuova istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se non ne esiste ancora una.  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)



