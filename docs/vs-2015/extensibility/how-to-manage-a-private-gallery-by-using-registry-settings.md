---
title: 'Procedura: gestire una raccolta privata mediante le impostazioni del Registro di sistema | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 020754fb1ddb020e120ba11e8aa3ec8d97206603
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852297"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Procedura: gestire una raccolta privata mediante le impostazioni del Registro di sistema
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se sei un amministratore o lo sviluppatore di un'estensione della Shell isolata, è possibile controllare l'accesso per i controlli, modelli e strumenti di Visual Studio Gallery, la raccolta di esempi o raccolte private. Per rendere una raccolta disponibile o non disponibile, creare un file. pkgdef che descrive le chiavi del Registro di sistema modificato e i relativi valori.  
  
## <a name="managing-private-galleries"></a>La gestione di raccolte Private  
 È possibile creare un file con estensione pkgdef per controllare l'accesso alle raccolte in più computer. Questo file deve avere il formato seguente.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Il `Repositories` chiave fa riferimento alla raccolta per essere abilitati o disabilitati. Visual Studio Gallery e la raccolta di esempi usano il repository seguente GUID:  
  
- Visual Studio Gallery: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
- Raccolta di esempi: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  Il `Disabled` valore è facoltativo. Per impostazione predefinita, una raccolta è abilitata.  
  
  Il `Priority` valore determina l'ordine in cui le raccolte disponibili sono elencate nella finestra di dialogo Opzioni. Raccolta di Visual Studio ha priorità 10 e la raccolta di esempi ha priorità 20. Raccolte private avviare con priorità 100. Se diverse raccolte hanno lo stesso valore di priorità, l'ordine in cui vengono visualizzati è determinato dai valori dei relativi localizzata `DisplayName` attributi.  
  
  Il `Protocol` valore è obbligatorio per le raccolte basate su Atom o basata su SharePoint.  
  
  Sia `DisplayName`, o entrambe `DisplayNameResourceID` e `DisplayNamePackageGuid`, deve essere specificato. Se si specifica all, il `DisplayNameResourceID` e `DisplayNamePackageGuid` coppia viene utilizzata.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Disabilitare la raccolta di Visual Studio usando un File con estensione pkgdef  
 È possibile disabilitare una raccolta in un file. pkgdef. La voce seguente disabilita la raccolta di Visual Studio:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 La voce seguente disabilita la raccolta di esempi:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolte private](../extensibility/private-galleries.md)

