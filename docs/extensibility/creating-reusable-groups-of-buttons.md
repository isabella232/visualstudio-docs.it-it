---
title: Creazione di gruppi riutilizzabili di pulsanti | Microsoft Docs
description: Informazioni su come creare un gruppo di comandi, ovvero una raccolta di comandi che vengono visualizzati insieme in un menu o in una barra degli strumenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5ef9e4c78fcd4bfe22ba6bcffcb2fe41d1a7dda2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057993"
---
# <a name="create-reusable-groups-of-buttons"></a>Creare gruppi riutilizzabili di pulsanti
Un gruppo di comandi è una raccolta di comandi che vengono sempre visualizzati insieme in un menu o in una barra degli strumenti. Qualsiasi gruppo di comandi può essere usato di nuovo assegnandolo a menu padre diversi nella sezione CommandPlacements del file *con estensione vsct.*

 I gruppi di comandi contengono in genere pulsanti, ma possono anche contenere altri menu o caselle combinate.

## <a name="to-create-a-reusable-group-of-buttons"></a>Per creare un gruppo riutilizzabile di pulsanti

1. Creare un progetto VSIX denominato `ReusableButtons` . Per altre informazioni, vedere [Creare un'estensione con un comando di menu.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. All'apertura del progetto, aggiungere un modello di elemento di comando personalizzato **denominato ReusableCommand.** Nella finestra di **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento.** Nella finestra **di dialogo Aggiungi nuovo** elemento passare a **Estendibilità di Visual C#**  >   e selezionare **Comando personalizzato.** Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in *ReusableCommand.cs*.

3. Nel file *con estensione vsct* passare alla sezione Symbols (Simboli) e trovare l'elemento GuidSymbol che contiene i gruppi e i comandi per il progetto. Deve essere denominato guidReusableCommandPackageCmdSet.

4. Aggiungere un IDSymbol per ogni pulsante che verrà aggiunto al gruppo, come nell'esempio seguente.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Per impostazione predefinita, il modello di elemento di comando crea un gruppo denominato **MyMenuGroup** e un pulsante con il nome specificato, insieme a una voce IDSymbol per ognuno.

5. Nella sezione Gruppi creare un elemento Group con gli stessi attributi GUID e ID di quelli specificati nella sezione Simboli. È anche possibile usare un gruppo esistente o la voce fornita dal modello di comando, come nell'esempio seguente. Questo gruppo viene visualizzato **nel** menu Strumenti

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Per creare un gruppo di pulsanti da riutilizzare

1. È possibile inserire un comando o un menu in un gruppo usando il gruppo come elemento padre nella definizione del comando o del menu oppure inserendo il comando o il menu nel gruppo usando la sezione CommandPlacements.

     Nella sezione Pulsanti definire un pulsante con il gruppo come padre oppure usare il pulsante fornito dal modello di pacchetto, come illustrato nell'esempio seguente.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Se un pulsante deve essere visualizzato in più di un gruppo, crearne una voce nella sezione CommandPlacements, che deve essere posizionata dopo la sezione Comandi. Impostare gli attributi GUID e ID dell'elemento CommandPlacement in modo che corrispondano a quelli del pulsante che si vuole posizionare, quindi impostare il GUID e l'ID del relativo elemento Parent su quelli del gruppo di destinazione, come illustrato nell'esempio seguente.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Il valore del campo Priorità determina la posizione del comando nel nuovo gruppo di comandi. Le priorità impostate nell'elemento CommandPlacement sostituiscono quelle impostate nella definizione dell'elemento. I comandi con valori di priorità più bassi vengono visualizzati prima dei comandi con valori di priorità più elevati. Sono consentiti valori di priorità duplicati, ma la posizione relativa dei comandi con lo stesso valore di priorità non può essere garantita perché l'ordine in cui il **comando devenv /setup** crea l'interfaccia finale dal Registro di sistema potrebbe non essere coerente.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Per inserire un gruppo riutilizzabile di pulsanti in un menu

1. Creare una voce nella `CommandPlacements` sezione . Impostare il GUID e l'ID dell'elemento su quelli del gruppo e impostare il GUID e l'ID padre su `CommandPlacement` quelli del percorso di destinazione.

    La sezione CommandPlacements deve essere posizionata subito dopo la sezione Comandi:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Un gruppo di comandi può essere incluso in più di un menu. Il menu padre può essere uno creato, uno fornito da (come descritto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in *ShellCmdDef.vsct* o *SharedCmdDef.vsct)* o uno definito in un altro VSPackage. Il numero di livelli padre è illimitato, purché il menu padre sia connesso a o a un menu di scelta rapida visualizzato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da un pacchetto VSPackage.

    Nell'esempio seguente il gruppo viene Esplora soluzioni **barra** degli strumenti, a destra degli altri pulsanti.

   ```xml
   <CommandPlacements>
       <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">
         <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
       </CommandPlacement>
   </CommandPlacements>
   ```

   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"
         priority="0x605">
       <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />
     </CommandPlacement>
   </CommandPlacements>

   ```
