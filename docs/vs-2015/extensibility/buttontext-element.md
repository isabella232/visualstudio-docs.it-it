---
title: Elemento ButtonText | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef22471d20df5582fec96c8a685029a1d475a4a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184570"
---
# <a name="buttontext-element"></a>Elemento ButtonText
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo campo consente di specificare il testo visualizzato in vari menu. Per impostazione predefinita, l' `ButtonText` elemento viene visualizzato nei controller di menu. L' `ButtonText` elemento diventa anche il valore predefinito se gli altri campi di testo sono vuoti. L' `ButtonText` elemento non può essere vuoto anche se gli altri campi di testo sono specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Strings](../extensibility/strings-element.md)|Raggruppa gli elementi di testo, ad esempio `ButtonText` e `CommandName` .|  
  
## <a name="text-value"></a>Valore di testo  
 Il valore di testo dell' `ButtonText` elemento fornisce il testo visualizzato per le voci di menu, le combinazioni e altri elementi dell'interfaccia utente con testo visibile.  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
