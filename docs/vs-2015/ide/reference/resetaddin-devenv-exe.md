---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9958e6e9a540dce1a405df8991780600b8f4a702
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665594"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rimuove i comandi e l'interfaccia utente dei comandi associata al componente aggiuntivo specificato.

## <a name="syntax"></a>Sintassi

```
Devenv /ResetAddin AddIn
```

## <a name="arguments"></a>Argomenti
 `AddIn` Facoltativo. Nome del comando del componente aggiuntivo.

## <a name="remarks"></a>Osservazioni
 Per impostazione predefinita, il nome del comando del componente aggiuntivo è uguale a *\<AddInSolutionName>* . Connect<em>. \<AddInSolutionName> </em>e viene visualizzato in Connect.cs come `commandName` parametro del `Exec` metodo. È anche possibile verificare il nome del comando digitando l'inizio del nome del componente aggiuntivo nella finestra dei comandi in Visual Studio e usando Intellisense per completarlo.

## <a name="example"></a>Esempio
 L'esempio seguente avvia Visual Studio e impedisce l'esecuzione all'avvio del componente aggiuntivo `MyAddin`.

```
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin
```

## <a name="see-also"></a>Vedere anche
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [devenv opzioni della riga di comando](../../ide/reference/devenv-command-line-switches.md)
