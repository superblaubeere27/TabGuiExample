# TabGuiExample

A simple TabGui for Minecraft.

```java
HashMap<ModuleCategory, List<Module>> moduleCategoryMap = new HashMap<>();

for (Module module : ModuleManager.getModules()) {
	if (!moduleCategoryMap.containsKey(module.getModuleCategory())) {
		moduleCategoryMap.put(module.getModuleCategory(), new ArrayList<>());
	}

	moduleCategoryMap.get(module.getModuleCategory()).add(module);
}

for (Map.Entry<ModuleCategory, List<Module>> moduleCategoryListEntry : moduleCategoryMap.entrySet()) {
	Tab<Module> tab = new Tab<>(moduleCategoryListEntry.getKey().getName());

	for (Module module : moduleCategoryListEntry.getValue()) {
		tab.addSubTab(new SubTab<>(module.getModuleName(), subTab -> subTab.getObject().setState(!subTab.getObject().getState()), module));
	}

	tabGui.addTab(tab);
}
```
