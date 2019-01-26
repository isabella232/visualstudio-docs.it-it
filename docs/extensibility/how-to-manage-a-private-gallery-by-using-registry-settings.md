---
title: 'Procedura: Gestire una raccolta privata mediante le impostazioni del Registro di sistema | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d75976ba9c677bb9b8f6c32623f81834471e10a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021520"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Procedura: Gestire una raccolta privata mediante le impostazioni del Registro di sistema
Se sei un amministratore o lo sviluppatore di un'estensione della Shell isolata, è possibile controllare l'accesso per i controlli, modelli e strumenti di Visual Studio Gallery, la raccolta di esempi o raccolte private. Per configurare una raccolta disponibile o non disponibile, creare un *pkgdef* file che descrive le chiavi del Registro di sistema modificato e i relativi valori.  
  
## <a name="manage-private-galleries"></a>Gestire raccolte private  
 È possibile creare un *pkgdef* file per controllare l'accesso alle raccolte in più computer. Questo file deve avere il formato seguente.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
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