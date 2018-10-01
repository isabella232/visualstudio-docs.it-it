---
title: Elemento Button | Microsoft Docs
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
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad49fd053a10938dcc9f038ff7385bcd93c6253f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518503"
---
# <a name="button-element"></a>Elemento Button
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [elemento pulsante](https://docs.microsoft.com/visualstudio/extensibility/button-element).  
  
Definisce un elemento che l'utente può interagire con. Pulsanti possono essere di tipi diversi: pulsante MenuButton e SplitDropDown.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. GUID dell'identificatore di comando/ID GUID.|  
|ID|Obbligatorio. ID dell'identificatore di comando/ID GUID.|  
|priority|Facoltativo. Valore numerico che specifica la priorità.|  
|tipo|Facoltativo. Valore enumerato che specifica il tipo di pulsante.<br /><br /> Se non viene specificato, viene utilizzata sul pulsante.<br /><br /> Button<br /> Comando standard che viene visualizzato nelle barre degli strumenti (in genere come un pulsante originalissima), i menu e menu di scelta rapida.<br /><br /> MenuButton<br /> Una voce di menu che non viene eseguito un comando, ma produce un altro menu.<br /><br /> SplitDropDown<br /> Controlli, ad esempio i pulsanti di annullamento e ripristino sulla barra degli strumenti standard in Microsoft Word.|  
|Condizione|Facoltativo. Visualizzare [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Parent](../extensibility/parent-element.md)|Facoltativo. L'elemento padre del pulsante.|  
|[Elemento Icon](../extensibility/icon-element.md)|Facoltativo. L'icona associata al pulsante.|  
|[Elemento CommandFlag](../extensibility/command-flag-element.md)|Obbligatorio. I valori CommandFlag validi per un pulsante sono come indicato di seguito.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Elemento Strings](../extensibility/strings-element.md)|Obbligatorio. L'elemento figlio [elemento ButtonText](../extensibility/buttontext-element.md) deve essere definito.|  
|Annotazione|Commento facoltativo.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Buttons](../extensibility/buttons-element.md)|Raggruppa gli elementi di pulsante.|  
  
## <a name="example"></a>Esempio  
 L'esempio seguente definisce un pulsante in un file con estensione vsct.  
   
 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

