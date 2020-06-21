# SubModule (XML)

## Описание Элементов

* `Name` - Название вашего Модуля
* `Id` - Идентификатор вашего Модуля (не используйте в названии пробелы).
* `Version` - Текущая версия вашего Модуля.
* `SinglePlayerModule` - Указание на то, используется ли ваш Модуль для одиночной игры. Принимает true/false.
* `MultiPlayerModule` - Указание на то, используется ли ваш Модуль для сетевой игры. Принимает true/false.
* `DependedModules` - Модули-зависимости, наличие которых требуется вашему Модулю для правильной работы.
* `SubModules` - Подмодули (DLLs), из которых состоят ваши модули.
* `Xmls` - содержит пути к XML файлам в каталоге(ах) ModuleData.

## Important

XML файлы двух разных модов (или одного и того же мода), но с одинаковыми id, объеденяются в ассеты и не перезаписываются. Однако, если два объекта не имеют своих XML, но имеют одинаковый id, они перезаписывают друг друга в очереде загрузки Модулей, что отражается в лаунчере. Это может быть полезно для перезаписи нативных ассетов.

XMLs with the same id from two separate mods (or the same mod) will have their assets combined and **NOT** overwritten. However, if two objects within an XML have the same id (e.g. two items), they will Overwrite each other in ModLoading Order as seen in the Launcher. Knowing this can be useful for overwritting native assets.

На заметку! `MPClassDivisions` на данный момент сломан.

## Example

```xml
<Module>
    <Name value="My Module"/>
    <Id value="MyModule"/>
    <Version value="v1.0.0"/>
    <SingleplayerModule value="true"/>
    <MultiplayerModule value="false"/>
    <DependedModules>
        <DependedModule Id="Native"/>
        <DependedModule Id="SandBoxCore"/>
        <DependedModule Id="Sandbox"/>
        <DependedModule Id="CustomBattle"/>
        <DependedModule Id="StoryMode" />
    </DependedModules>
    <SubModules>
        <!-- The following SubModule element is optional. You can remove this portion if your mod does not have a DLL associated with it. -->
        <SubModule>
            <Name value="MySubModule"/>
            <!-- Path to the DLL File, if your Mod is called MyModule then it should be   -->
            <DLLName value="ExampleMod.dll"/>
            <SubModuleClassType value="ExampleMod.MySubModule"/>
            <Tags>
                <Tag key="DedicatedServerType" value="none" />
                <Tag key="IsNoRenderModeElement" value="false" />
            </Tags>
        </SubModule>
    </SubModules>
    <Xmls>
        <XmlNode>
            <XmlName id="Items" path="customitems"/>
        </XmlNode>  
        <XmlNode>
            <XmlName id="SPCultures" path="customcultures"/>
        </XmlNode>
        <XmlNode>
            <XmlName id="NPCCharacters" path="customcharacters"/>
        </XmlNode>
    </Xmls>
</Module>
```
