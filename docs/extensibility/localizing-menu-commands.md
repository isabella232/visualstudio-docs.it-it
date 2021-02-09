---
title: Localizzazione dei comandi di menu | Microsoft Docs
description: Informazioni su come fornire il testo localizzato per i comandi di menu e barre degli strumenti creando file con estensione vsct localizzati e file con estensione resx localizzati per il pacchetto VSPackage.
ms.custom: SEO-VS-2020
ms.date: 10/08/2019
ms.topic: how-to
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af86f64935d4e99d4c1245669505fcef8ce7ec1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893620"
---
# <a name="localize-menu-commands"></a>Comandi di menu Localize

È possibile fornire il testo localizzato per i comandi di menu e barre degli strumenti creando file con *estensione vsct* localizzati e file con *estensione resx* localizzati per il pacchetto VSPackage, quindi aggiornando i file di progetto per incorporare le modifiche.

Per informazioni su come localizzare l'esperienza di installazione, vedere [localizzare i pacchetti VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Localizzare i nomi dei comandi

Nei pacchetti VSPackage, i comandi di menu e i pulsanti della barra degli strumenti sono definiti nel file con *estensione vsct* .

1. In **Esplora soluzioni** modificare il nome del file con *estensione vsct* da *filename. vsct* a *filename. en-US. vsct*.

2. Creare una copia di *filename. en-US. vsct* per ogni lingua localizzata.

    Denominare ogni copia *filename. { Impostazioni locali}. vsct*, dove *{locale}* è un nome di impostazioni cultura specifico. Per un elenco di valori dei nomi delle impostazioni cultura, vedere [ID delle impostazioni locali assegnati da Microsoft](/windows/uwp/publish/supported-languages).

    *Nome file. I file locale. vsct* conterranno il testo del menu localizzato per il pacchetto.

3. Aprire ogni *nome file. File locale. vsct* per localizzare il testo.

   1. Modificare i valori dell'elemento [ButtonText](../extensibility/buttontext-element.md) nel modo appropriato per la lingua specifica.

   2. Se si forniranno icone localizzate, modificare i valori [bitmap](../extensibility/bitmap-element.md) in modo che puntino ai file di destinazione.

      Nell'esempio seguente viene illustrato il testo del pulsante inglese e spagnolo per un comando per aprire una finestra degli strumenti di Esplora albero.

      [*FamilyTree. en-US. vsct*]

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

    [*FamilyTree.es-es. vsct*]

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

Le risorse di testo diverse dai nomi dei comandi sono definite nei file di risorse (con *estensione resx*).

1. Rinominare *VSPackage. resx* in *VSPackage. en-US. resx*.

2. Creare una copia del file *VSPackage. en-US. resx* per ogni lingua localizzata.

     Assegnare a ogni copia il nome *VSPackage. { Impostazioni locali}. resx*, dove *{locale}* è un nome di impostazioni cultura specifico.

3. Rinominare *Resources. resx* in *Resources. en-US. resx*.

4. Creare una copia del file *Resources. en-US. resx* per ogni lingua localizzata.

     Assegnare un nome a ogni risorsa di copia *. { Impostazioni locali}. resx*, dove *{locale}* è un nome di impostazioni cultura specifico.

5. Aprire ogni file *. resx* per modificare i valori stringa in base alla lingua e alle impostazioni cultura specifiche. Nell'esempio seguente viene illustrata la definizione di risorsa localizzata per la barra del titolo di una finestra degli strumenti.

     [*Resources. en-US. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-es. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Incorporare le risorse localizzate nel progetto

Per incorporare le risorse localizzate, è necessario modificare il file *AssemblyInfo.cs* e il file di progetto.

1. Dal nodo **Proprietà** in **Esplora soluzioni** aprire *AssemblyInfo.cs* o *AssemblyInfo. vb* nell'editor.

2. Aggiungere la voce seguente.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     In questo modo viene impostata la lingua predefinita per l'inglese (Stati Uniti).

3. Scaricare il progetto.

4. Aprire il file di progetto nell'editor.

5. Nell'elemento radice `Project` aggiungere un `PropertyGroup` elemento con un `UICulture` elemento che corrisponde alla lingua predefinita.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     In questo modo, US English viene impostato come impostazioni cultura dell'interfaccia utente predefinite per i controlli Windows Presentation Foundation (WPF).

6. Individuare l' `ItemGroup` elemento che contiene `EmbeddedResource` gli elementi.

7. Nell' `EmbeddedResource` elemento che chiama *VSPackage. en-US. resx*, sostituire l' `ManifestResourceName` elemento con un `LogicalName` elemento impostato su `VSPackage.en-US.Resources` , come indicato di seguito:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Per ogni lingua localizzata, copiare l'  `EmbeddedResource` elemento per `VsPackage.en-US` e impostare l'attributo **include** e l'elemento **LogicalName** della copia nelle impostazioni locali di destinazione.

9. Per ogni elemento localizzato `VSCTCompile` , aggiungere un `ResourceName` elemento a cui punta `Menus.ctmenu` , come illustrato nell'esempio seguente:

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

## <a name="see-also"></a>Vedi anche

- [Estendi menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Globalizzare e localizzare le applicazioni](../ide/globalizing-and-localizing-applications.md)
