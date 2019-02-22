---
title: Utilità CreatePkgDef | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96b0343cd088a8d608cd3503162bf7fa737b79f4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602442"
---
# <a name="createpkgdef-utility"></a>Utilità CreatePkgDef
Accetta un file con estensione dll per un'estensione di Visual Studio come parametro e crea un *pkgdef* file di accompagnamento per il *DLL* file. Il *pkgdef* file contiene tutte le informazioni che verrebbe scritto nel Registro di sistema in caso contrario, quando è installata l'estensione.

> [!NOTE]
>  Creare la maggior parte dei modelli di progetto che sono inclusi automaticamente in Visual Studio SDK *pkgdef* file come parte del processo di compilazione. Questo documento è destinato a utenti che desiderano creare manualmente i pacchetti o convertire i pacchetti esistenti per usare *pkgdef* distribuzione.

## <a name="syntax"></a>Sintassi

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argomenti
 **/ out =&lt;nomefile&gt;**  necessari. Imposta il nome del *pkgdef* del file di output &lt;FileName&gt;.

 **/ codebase** facoltativo. Forza la registrazione con il **CodeBase** utilità.

 **/assembly** forza la registrazione con il **Assembly** utilità.

 **&lt;AssemblyPath&gt;**  il percorso del *DLL* file da cui si desidera generare il *pkgdef*.

## <a name="remarks"></a>Note
 Distribuzione di un'estensione usando *pkgdef* file sostituisce i requisiti del Registro di sistema le versioni precedenti di Visual Studio.

 Il *pkgdef* file devono essere installati in una delle seguenti posizioni:

- *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\*

- *%VSInstallDir%\Common7\IDE\Extensions\\*

  Se la cartella di installazione *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\*, l'estensione verrà riconosciuto da Visual Studio, ma verrà disabilitata per impostazione predefinita. L'utente può abilitare l'estensione usando **estensioni e aggiornamenti**.

  Se la cartella di installazione *%vsinstalldir%\Common7\IDE\Extensions\\*, l'estensione sia abilitata per impostazione predefinita.

> [!NOTE]
>  Il **estensioni e aggiornamenti** strumento non può essere usato per accedere a un'estensione a meno che non viene installato come parte di un pacchetto VSIX.

## <a name="see-also"></a>Vedere anche
- [Utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)