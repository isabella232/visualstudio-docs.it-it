---
title: Utilità CreatePkgDef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 010ee75efd84f016b0eb68fa9f715102026a4678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839340"
---
# <a name="createpkgdef-utility"></a>Utilità CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Accetta un file con estensione dll per un'estensione di Visual Studio come parametro e crea un file pkgdef per accompagnare il file. dll. Il file. pkgdef contiene tutte le informazioni che altrimenti verrebbero scritte nel registro di sistema durante l'installazione dell'estensione.  
  
> [!NOTE]
> La maggior parte dei modelli di progetto inclusi in Visual Studio SDK crea automaticamente i file con estensione pkgdef come parte del processo di compilazione. Questo documento è destinato agli utenti che desiderano creare pacchetti manualmente o a convertire i pacchetti esistenti in modo da usare la distribuzione. pkgdef.  
  
## <a name="syntax"></a>Sintassi  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argomenti  
 /out =`FileName`  
 Obbligatorio. Imposta il nome del file di output con estensione pkgdef su `FileName` .  
  
 /codebase  
 Facoltativo. Forza la registrazione con l'utilità codebase.  
  
 /assembly  
 Forza la registrazione con l'utilità di assembly.  
  
 `AssemblyPath`  
 Percorso del file con estensione dll da cui si desidera generare il file con estensione pkgdef.  
  
## <a name="remarks"></a>Commenti  
 La distribuzione di estensioni con i file pkgdef sostituisce i requisiti del registro di sistema delle versioni precedenti di Visual Studio.  
  
 I file con estensione pkgdef devono essere installati in uno dei percorsi seguenti:%localappdata%\Microsoft\Visual Studio\14.0\Extensions\ o%vsinstalldir%\Common7\IDE\Extensions \\ . Se la cartella di installazione è%localappdata%\Microsoft\Visual Studio\14.0\Extensions \\ , l'estensione verrà riconosciuta da Visual Studio, ma verrà disabilitata per impostazione predefinita. L'utente può abilitare l'estensione tramite **estensioni e aggiornamenti**. Se la cartella di installazione è%vsinstalldir%\Common7\IDE\Extensions \\ , l'estensione è abilitata per impostazione predefinita.  
  
> [!NOTE]
> Lo strumento **estensioni e aggiornamenti** non può essere usato per accedere a un'estensione a meno che non sia installato come parte di un pacchetto VSIX.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
