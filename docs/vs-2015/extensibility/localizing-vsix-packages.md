---
title: Localizzazione di pacchetti VSIX | Microsoft Docs
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
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f6bc666e244fed2bc2922ce4878434730a643e5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750592"
---
# <a name="localizing-vsix-packages"></a>Localizzazione di pacchetti VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Creando un file vsixlangpack per ogni lingua di destinazione e inserendo i file nella cartella corretta, è possibile localizzare un pacchetto VSIX. Quando viene installato un pacchetto di aggiornamento, viene visualizzato il nome localizzato dell'estensione con una descrizione localizzata. Se si specifica un file di licenza localizzata o un URL che punta alle informazioni localizzate, vengono anche visualizzate.  
  
 Se il contenuto del pacchetto VSIX include un pacchetto VSPackage che aggiunge i comandi di menu o altra interfaccia utente, vedere [localizzazione di comandi di Menu](../extensibility/localizing-menu-commands.md) per informazioni sulla localizzazione dei nuovi elementi dell'interfaccia utente.  
  
## <a name="directory-structure"></a>Struttura di directory  
 Quando un utente installa un'estensione **estensioni e aggiornamenti** controlla il livello principale del pacchetto VSIX per una cartella il cui nome corrisponde le impostazioni locali di Visual Studio del computer di destinazione. Se **estensioni e aggiornamenti** trova un con estensione vsixlangpack file nella cartella, lo sostituisce con i valori localizzati in tale file per i valori corrispondenti nel file di estensione vsixmanifest. Questi valori vengono visualizzati quando viene installato l'estensione. Nell'esempio seguente mostra la struttura di directory per un pacchetto VSIX che viene localizzato in spagnolo (es-ES) e francese (fr-FR).  
  
 MyExtension.dll  
  
 Extension. vsixmanifest  
  
 [Content_Types] XML  
  
 es-ES  
  
 Vsixlangpack  
  
 fr-FR  
  
 Vsixlangpack  
  
> [!NOTE]
>  I modelli di progetto supportato da VSIX di [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] generare un manifesto VSIX e assegnargli il nome vsixmanifest. Quando Visual Studio compila il progetto, verrà copiato il contenuto del file in Extension. vsixmanifest nel pacchetto VSIX.  
  
## <a name="the-extensionvsixlangpack-file"></a>Il File vsixlangpack  
 Il file vsixlangpack segue il [Schema del Language Pack VSIX](../extensibility/vsx-language-pack-schema-reference.md). Questo schema ha un [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) elemento radice e i quattro elementi figlio: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), e [licenza](../extensibility/license-element-vsix-language-pack-schema.md). Tali elementi figlio corrispondano per il `Name`, `Description`, `MoreInfoURL`, e `License` elementi figlio del `Identifier` elemento del file Extension. vsixmanifest.  
  
 Quando si crea un file vsixlangpack, è necessario impostare il `Include in Vsix` proprietà `true`. In caso contrario, il testo di installazione localizzata verrà ignorato.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Per impostare l'inclusione in proprietà Vsix  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic su file vsixlangpack e quindi fare clic su **proprietà**.  
  
2.  Nella griglia delle proprietà, fare clic su **Includi in Vsix**e impostarne il valore su `true`.  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
 L'esempio seguente illustra le parti pertinenti di un file Extension. vsixmanifest, insieme al file vsixlangpack corrispondente per lo spagnolo. I valori dal language pack di sostituiscono i valori dal manifesto se le impostazioni locali di Visual Studio del computer di destinazione sono impostata sullo spagnolo.  
  
### <a name="code"></a>Codice  
 [Extension. vsixmanifest]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 [Vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Modello di progetto VSIX](../extensibility/vsix-project-template.md)

