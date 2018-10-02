---
title: Elemento ButtonText | Microsoft Docs
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
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7cbf92a762fd3fce80e7f59e77c03c8cd81cc22
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518199"
---
# <a name="buttontext-element"></a>Elemento ButtonText
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [elemento ButtonText](https://docs.microsoft.com/visualstudio/extensibility/buttontext-element).  
  
Questo campo consente di specificare il testo visualizzato nei vari menu. Per impostazione predefinita, il `ButtonText` elemento compare in un controller di menu. Il `ButtonText` elemento diventa l'impostazione predefinita anche se gli altri campi di testo sono vuoti. Il `ButtonText` elemento non può essere vuoto anche se vengono specificati gli altri campi di testo.  
  
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
|[Elemento Strings](../extensibility/strings-element.md)|Raggruppa gli elementi di testo, ad esempio `ButtonText` e `CommandName`.|  
  
## <a name="text-value"></a>Valore di testo  
 Il valore del testo di `ButtonText` elemento fornisce il testo visualizzato per le voci di menu, combos e altri elementi dell'interfaccia utente con testo visibile.  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

