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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441495"
---
# <a name="createpkgdef-utility"></a>Utilità CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Accetta un file con estensione dll per un'estensione di Visual Studio come parametro e crea un file con estensione pkgdef per accompagnare il file DLL. Il file con estensione pkgdef contiene tutte le informazioni che verrebbe scritto nel Registro di sistema in caso contrario, quando è installata l'estensione.  
  
> [!NOTE]
> La maggior parte dei modelli di progetto che sono inclusi automaticamente in Visual Studio SDK creare file con estensione pkgdef come parte del processo di compilazione. Questo documento è destinato a coloro che desiderano creare manualmente i pacchetti o convertire i pacchetti esistenti per usare la distribuzione con estensione pkgdef.  
  
## <a name="syntax"></a>Sintassi  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argomenti  
 /out=`FileName`  
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
> Il **estensioni e aggiornamenti** strumento non può essere usato per accedere a un'estensione a meno che non viene installato come parte di un pacchetto VSIX.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
