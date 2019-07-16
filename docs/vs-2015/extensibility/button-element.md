---
title: Elemento Button | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58f63968ed02f49b0ccfa4dda24f684fed339bc4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184543"
---
# <a name="button-element"></a>Elemento Button
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definisce un elemento che l'utente può interagire con. Pulsanti possono essere di tipi diversi: Pulsante MenuButton e SplitDropDown.  
  
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
|GUID|Richiesto. GUID dell'identificatore di comando/ID GUID.|  
|id|Richiesto. ID dell'identificatore di comando/ID GUID.|  
|priorità|facoltativo. Valore numerico che specifica la priorità.|  
|type|facoltativo. Valore enumerato che specifica il tipo di pulsante.<br /><br /> Se non viene specificato, viene utilizzata sul pulsante.<br /><br /> Button<br /> Comando standard che viene visualizzato nelle barre degli strumenti (in genere come un pulsante originalissima), i menu e menu di scelta rapida.<br /><br /> MenuButton<br /> Una voce di menu che non viene eseguito un comando, ma produce un altro menu.<br /><br /> SplitDropDown<br /> Controlli, ad esempio i pulsanti di annullamento e ripristino sulla barra degli strumenti standard in Microsoft Word.|  
|Condizione|facoltativo. Visualizzare [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Parent](../extensibility/parent-element.md)|facoltativo. L'elemento padre del pulsante.|  
|[Elemento Icon](../extensibility/icon-element.md)|facoltativo. L'icona associata al pulsante.|  
|[Elemento CommandFlag](../extensibility/command-flag-element.md)|Richiesto. I valori CommandFlag validi per un pulsante sono come indicato di seguito.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Elemento Strings](../extensibility/strings-element.md)|Richiesto. L'elemento figlio [elemento ButtonText](../extensibility/buttontext-element.md) deve essere definito.|  
|Annotazione|Commento facoltativo.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|DESCRIZIONE|  
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
