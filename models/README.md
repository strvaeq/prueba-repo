# Models and manufacturing

The included [robotek_description](../src/robotek_description/package.xml) supplies URDF and STL meshes used to represent the car in simulation. Those assets are retained in their package so resource paths continue to work.

| Asset class | Location / availability | Purpose |
|---|---|---|
| Robot description and simulation meshes | src/robotek_description | Simulation and geometric inspection |
| Editable current manufacturing CAD | Not supplied | Modify dimensions and reconstruct the physical design |
| Fabrication exports | Not verified for current assembly | STL/STEP/DXF as appropriate to the process |
| Assembly drawings and hardware list | Not supplied | Fasteners, tolerances and assembly order |

KMIDS' separation of editable CAD and fabrication exports is adopted as an indexing principle. Its vehicle models are not included: they describe a different robot. When current CAD is supplied, use part IDs shared by the BOM and assembly guide. Record units, material, quantity, orientation and any important fabrication setting. Label simulation-only assets explicitly.
