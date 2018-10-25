---
title: 'Procedura: gestire una raccolta privata mediante le impostazioni del Registro di sistema | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2351c048576d6cf0e93515df8bdce34eef09bfc8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854663"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Procedura: gestire una raccolta privata mediante le impostazioni del Registro di sistema
Se sei un amministratore o lo sviluppatore di un'estensione della Shell isolata, è possibile controllare l'accesso per i controlli, modelli e strumenti di Visual Studio Gallery, la raccolta di esempi o raccolte private. Per configurare una raccolta disponibile o non disponibile, creare un *pkgdef* file che descrive le chiavi del Registro di sistema modificato e i relativi valori.  
  
## <a name="manage-private-galleries"></a>Gestire raccolte private  
 È possibile creare un *pkgdef* file per controllare l'accesso alle raccolte in più computer. Questo file deve avere il formato seguente.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Il `Repositories` chiave fa riferimento alla raccolta per essere abilitati o disabilitati. Visual Studio Gallery e la raccolta di esempi usano il repository seguente GUID:  
  
- Visual Studio Gallery: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
- Raccolta di esempi: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  Il `Disabled` valore è facoltativo. Per impostazione predefinita, una raccolta è abilitata.  
  
  Il `Priority` valore determina l'ordine in cui sono elencate le raccolte nel **opzioni** nella finestra di dialogo. Raccolta di Visual Studio ha priorità 10 e la raccolta di esempi ha priorità 20. Raccolte private avviare con priorità 100. Se diverse raccolte hanno lo stesso valore di priorità, l'ordine in cui vengono visualizzati è determinato dai valori dei relativi localizzata `DisplayName` attributi.  
  
  Il `Protocol` valore è obbligatorio per le raccolte basate su Atom o basata su SharePoint.  
  
  Sia `DisplayName`, o entrambe `DisplayNameResourceID` e `DisplayNamePackageGuid`, deve essere specificato. Se si specifica all, il `DisplayNameResourceID` e `DisplayNamePackageGuid` coppia viene utilizzata.  
  
## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Disabilitare la raccolta di Visual Studio usando un file con estensione pkgdef  
 È possibile disabilitare una raccolta in una *pkgdef* file. La voce seguente disabilita la raccolta di Visual Studio:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 La voce seguente disabilita la raccolta di esempi:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolte private](../extensibility/private-galleries.md)