---
title: 'Procedura: gestire una raccolta privata utilizzando le impostazioni del registro di sistema | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a55b7aa486edfd3775b12dca9d143c2e5f280884
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204162"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Procedura: Gestire una raccolta privata tramite le impostazioni del Registro di sistema
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si è un amministratore o lo sviluppatore di un'estensione della shell isolata, è possibile controllare l'accesso ai controlli, ai modelli e agli strumenti di Visual Studio Gallery, della raccolta di esempi o delle raccolte private. Per rendere una raccolta disponibile o non disponibile, creare un file con estensione pkgdef che descrive le chiavi del registro di sistema modificate e i relativi valori.  
  
## <a name="managing-private-galleries"></a>Gestione delle raccolte private  
 È possibile creare un file con estensione pkgdef per controllare l'accesso alle raccolte su più computer. Questo file deve avere il formato seguente.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 La `Repositories` chiave fa riferimento alla raccolta da abilitare o disabilitare. Visual Studio Gallery e la raccolta di esempi usano i seguenti GUID del repository:  
  
- Raccolta di Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
- Raccolta di esempi: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  Il `Disabled` valore è facoltativo. Per impostazione predefinita, la raccolta è abilitata.  
  
  Il `Priority` valore determina l'ordine in cui le raccolte sono elencate nella finestra di dialogo Opzioni. Visual Studio Gallery ha la priorità 10 e la raccolta di esempi ha priorità 20. Le raccolte private iniziano con la priorità 100. Se più raccolte hanno lo stesso valore di priorità, l'ordine in cui vengono visualizzate è determinato dai valori degli attributi localizzati `DisplayName` .  
  
  Il `Protocol` valore è obbligatorio per le raccolte basate su Atom o su SharePoint.  
  
  `DisplayName` `DisplayNameResourceID` È necessario specificare sia, sia che `DisplayNamePackageGuid` . Se vengono specificati tutti, `DisplayNameResourceID` `DisplayNamePackageGuid` viene utilizzata la coppia e.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Disabilitazione di Visual Studio Gallery tramite un file con estensione pkgdef  
 È possibile disabilitare una raccolta in un file con estensione pkgdef. La voce seguente Disabilita Visual Studio Gallery:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 La seguente voce Disabilita la raccolta di esempi:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolte private](../extensibility/private-galleries.md)
