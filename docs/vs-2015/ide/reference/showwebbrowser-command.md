---
title: Comando ShowWebBrowser| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c1fca2c1c1dde167c8028d6ad4d543e108a488b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798213"
---
# <a name="showwebbrowser-command"></a>Comando ShowWebBrowser
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Visualizza l'URL specificato in una finestra del Web browser all'interno o all'esterno dell'ambiente di sviluppo integrato (IDE).  
  
## <a name="syntax"></a>Sintassi  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## <a name="arguments"></a>Argomenti  
 `URL`  
 Obbligatorio. URL (Uniform Resource Locator) per il sito Web.  
  
## <a name="switches"></a>Opzioni  
 /new  
 Facoltativo. Specifica che la pagina venga visualizzata in una nuova istanza del Web browser.  
  
 /ext  
 Facoltativo. Specifica che la pagina venga visualizzata nel Web browser predefinito all'esterno dell'IDE.  
  
## <a name="remarks"></a>Note  
 L'alias per il comando **ShowWebBrowser** è **navigate** o **nav**.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra la home page di MSDN Online in un Web browser all'esterno dell'IDE. Se è già aperta un'istanza del Web browser, viene usata; in caso contrario, viene avviata una nuova istanza.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
