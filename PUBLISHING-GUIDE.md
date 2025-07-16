# Publishing pycrdt-sticky-xml to PyPI

## Prerequisites

1. Create a PyPI account at https://pypi.org/account/register/
2. Install build tools:
   ```bash
   pip install build twine
   ```

## Steps to Publish

1. **Update package imports** (if keeping as separate package):
   - Change all `pycrdt` imports to `pycrdt_sticky_xml` in Python files
   - Update the module name in pyproject.toml

2. **Use the sticky-xml configuration files**:
   ```bash
   cp pyproject-sticky-xml.toml pyproject.toml
   cp Cargo-sticky-xml.toml Cargo.toml
   cp README-sticky-xml.md README.md
   ```

3. **Build the package**:
   ```bash
   python -m build
   ```

4. **Test the package locally**:
   ```bash
   pip install dist/pycrdt_sticky_xml-*.whl
   python -c "from pycrdt_sticky_xml import XmlText; print('Import successful')"
   ```

5. **Upload to TestPyPI first** (recommended):
   ```bash
   twine upload --repository testpypi dist/*
   ```

6. **Upload to PyPI**:
   ```bash
   twine upload dist/*
   ```

## Alternative: Submit as Pull Request

Consider submitting this feature to the main pycrdt project:

1. Fork the original repository
2. Create a feature branch
3. Apply your changes
4. Submit a pull request with:
   - Description of the sticky_index feature for XML types
   - Tests showing the functionality
   - Documentation updates

This would benefit the entire pycrdt community and avoid fragmentation.