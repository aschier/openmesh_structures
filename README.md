OpenMesh Structures
===================

This library defines OpenMesh structures, which can be included in a CMake project.
By using the structures as library instead of defining them directly in a project,
multiple subprojects use a compatible structure instead of having different types even
when the definitions in the struct are the same.

The library uses CMake exported targets, so all you need is to use ``find_package`` and add
``openmesh_structures`` to your ``target_link_libraries``.

DoublePrecisionTraits
---------------------

A mesh traits struct, which uses double precision for vertex and texture coordinates.
The struct is added to the ``OpenMesh`` namespace as ``OpenMesh::DoublePrecisionTraits``.

**Usage:**

    #include <openmesh_doubleprecisiontraits.h>
    typedef OpenMesh::TriMesh_ArrayKernelT<OpenMesh::DoublePrecisionTraits> TriMesh;

**CMakeLists.txt Example:**

    find_package(openmesh_structures REQUIRED)
    add_binary(myproject myproject.cpp)
    target_link_libraries(myproject ${OPENMESH_LIBRARIES} openmesh_structures)

If you are not using CMake, just add the library directory to your include directories.
