---
title: Utilità CreatePkgDef | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec77937e18ab437107b0e9d269fb4b5c7c8e2381
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527701"
---
# <a name="createpkgdef-utility"></a>Utilità CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [utilità CreatePkgDef](https://docs.microsoft.com/visualstudio/extensibility/internals/createpkgdef-utility).  
  
Accetta un file con estensione dll per un'estensione di Visual Studio come parametro e crea un file con estensione pkgdef per accompagnare il file DLL. Il file con estensione pkgdef contiene tutte le informazioni che verrebbe scritto nel Registro di sistema in caso contrario, quando è installata l'estensione.  
  
> [!NOTE]
>  La maggior parte dei modelli di progetto che sono inclusi automaticamente in Visual Studio SDK creare file con estensione pkgdef come parte del processo di compilazione. Questo documento è destinato a coloro che desiderano creare manualmente i pacchetti o convertire i pacchetti esistenti per usare la distribuzione con estensione pkgdef.  
  
## <a name="syntax"></a>Sintassi  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argomenti  
 / out =`FileName`  
 Obbligatorio. Imposta il nome del file di output con estensione pkgdef per`FileName`.  
  
 /codebase  
 Facoltativo. Forza la registrazione dell'utente con l'utilità di base di codici.  
  
 /assembly  
 Forza la registrazione dell'utente con l'utilità di Assembly.  
  
 `AssemblyPath`  
 Il percorso del file con estensione dll da cui si desidera generare il pkgdef.  
  
## <a name="remarks"></a>Note  
 Distribuzione di un'estensione usando i file con estensione pkgdef sostituisce i requisiti del Registro di sistema le versioni precedenti di Visual Studio.  
  
 I file con estensione pkgdef devono essere installati in uno dei seguenti percorsi: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ o %vsinstalldir%\Common7\IDE\Extensions\\. Se la cartella di installazione è %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\, l'estensione verrà riconosciuto da Visual Studio, ma verrà disabilitata per impostazione predefinita. L'utente può abilitare l'estensione usando **estensioni e aggiornamenti**. Se la cartella di installazione è %vsinstalldir%\Common7\IDE\Extensions\\, l'estensione sia abilitata per impostazione predefinita.  
  
> [!NOTE]
>  Il **estensioni e aggiornamenti** strumento non può essere usato per accedere a un'estensione a meno che non viene installato come parte di un pacchetto VSIX.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)

