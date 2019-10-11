---
title: Localizzazione dei comandi di menu | Microsoft Docs
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b2b42143c2971bcbb172958b8da42a1e887e4699
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252633"
---
# <a name="localize-menu-commands"></a>Comandi di menu Localize

È possibile fornire il testo localizzato per i comandi di menu e barre degli strumenti creando file con *estensione vsct* localizzati e file con *estensione resx* localizzati per il pacchetto VSPackage, quindi aggiornando i file di progetto per incorporare le modifiche.

Per informazioni su come localizzare l'esperienza di installazione, vedere [localizzare i pacchetti VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Localizzare i nomi dei comandi

Nei pacchetti VSPackage, i comandi di menu e i pulsanti della barra degli strumenti sono definiti nel file con *estensione vsct* .

1. In **Esplora soluzioni**modificare il nome del file con *estensione vsct* da *filename. vsct* a *filename. en-US. vsct*.

2. Creare una copia di *filename. en-US. vsct* per ogni lingua localizzata.

    Denominare ogni copia *filename. { Impostazioni locali}. vsct*, dove *{locale}* è un nome di impostazioni cultura specifico. Per un elenco di valori dei nomi delle impostazioni cultura, vedere [ID delle impostazioni locali assegnati da Microsoft](/windows/uwp/publish/supported-languages).

    *Nome file. I file locale. vsct* conterranno il testo del menu localizzato per il pacchetto.

3. Aprire ogni *nome file. File locale. vsct* per localizzare il testo.

   1. Modificare i valori dell'elemento [ButtonText](../extensibility/buttontext-element.md) nel modo appropriato per la lingua specifica.

   2. Se si forniranno icone localizzate, modificare i valori [bitmap](../extensibility/bitmap-element.md) in modo che puntino ai file di destinazione.

      Nell'esempio seguente viene illustrato il testo del pulsante inglese e spagnolo per un comando per aprire una finestra degli strumenti di Esplora albero.

      [*FamilyTree.en-US.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Family Tree Explorer</ButtonText>
     </Strings>
   </Button>
   ```

    [*FamilyTree.es-ES.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Explorar el arbol genealogico</ButtonText>
     </Strings>
   </Button>
   ```

## <a name="localize-other-text-resources"></a>Localizzare altre risorse di testo

Le risorse di testo diverse dai nomi dei comandi sono definite nei file di risorse (con*estensione resx*).

1. Rinominare *VSPackage. resx* in *VSPackage. en-US. resx*.

2. Creare una copia del file *VSPackage. en-US. resx* per ogni lingua localizzata.

     Assegnare a ogni copia il nome *VSPackage. { Impostazioni locali}. resx*, dove *{locale}* è un nome di impostazioni cultura specifico.

3. Rinominare *Resources. resx* in *Resources. en-US. resx*.

4. Creare una copia del file *Resources. en-US. resx* per ogni lingua localizzata.

     Assegnare un nome a ogni risorsa di copia *. { Impostazioni locali}. resx*, dove *{locale}* è un nome di impostazioni cultura specifico.

5. Aprire ogni file *. resx* per modificare i valori stringa in base alla lingua e alle impostazioni cultura specifiche. Nell'esempio seguente viene illustrata la definizione di risorsa localizzata per la barra del titolo di una finestra degli strumenti.

     [*Resources.en-US.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Incorporare le risorse localizzate nel progetto

Per incorporare le risorse localizzate, è necessario modificare il file *AssemblyInfo.cs* e il file di progetto.

1. Dal nodo **Proprietà** in **Esplora soluzioni**aprire *AssemblyInfo.cs* o *AssemblyInfo. vb* nell'editor.

2. Aggiungere la voce seguente.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     In questo modo viene impostata la lingua predefinita per l'inglese (Stati Uniti).

3. Scaricare il progetto.

4. Aprire il file di progetto nell'editor.

5. Nell'elemento radice `Project` aggiungere un elemento `PropertyGroup` con un elemento `UICulture` corrispondente alla lingua predefinita.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     In questo modo, US English viene impostato come impostazioni cultura dell'interfaccia utente predefinite per i controlli Windows Presentation Foundation (WPF).

6. Individuare l'elemento `ItemGroup` che contiene gli elementi `EmbeddedResource`.

7. Nell'elemento `EmbeddedResource` che chiama *VSPackage. en-US. resx*, sostituire l'elemento `ManifestResourceName` con un elemento `LogicalName` impostato su `VSPackage.en-US.Resources`, come indicato di seguito:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Per ogni lingua localizzata, copiare l'elemento `EmbeddedResource` per `VsPackage.en-US` e impostare l'attributo **include** e l'elemento **LogicalName** della copia sulle impostazioni locali di destinazione.

9. Per ogni elemento `VSCTCompile` localizzato, aggiungere un elemento `ResourceName` che punta a `Menus.ctmenu`, come illustrato nell'esempio seguente:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Salvare il file di progetto e ricaricare il progetto.

11. Compilare il progetto.

     Viene creato un assembly principale e gli assembly di risorse per ogni lingua. Per informazioni sulla localizzazione del processo di distribuzione, vedere [localizzare i pacchetti VSIX](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Vedere anche
- [Estendi menu e comandi](../extensibility/extending-menus-and-commands.md)
- confronto tra @no__t e 0MenuCommands OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)
- [Globalizzare e localizzare le applicazioni](../ide/globalizing-and-localizing-applications.md)
