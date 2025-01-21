# cloudcoil.models.cert_manager

Versioned cert_manager models for cloudcoil.

## 🔧 Installation

Using [uv](https://github.com/astral-sh/uv) (recommended):

```bash
# Install with cert-manager support
uv add cloudcoil.models.cert_manager
```

Using pip:

```bash
pip install cloudcoil.models.cert_manager
```

## 💡 Examples

### Using cert-manager Models

```python
from cloudcoil import apimachinery
import cloudcoil.models.cert_manager.v1 as cm

# Create a Certificate
certificate = cm.Certificate(
    metadata=apimachinery.ObjectMeta(name="example-cert", namespace="default"),
    spec=cm.CertificateSpec(
        secret_name="example-cert-tls",
        issuer_ref=cm.IssuerRef(name="example-issuer"),
        dns_names=["example.com"]
    )
).create()

# List Certificates
for cert in cm.Certificate.list(namespace="default"):
    print(f"Found certificate: {cert.metadata.name}")

# Update a Certificate
certificate.spec.dns_names.append("www.example.com")
certificate.save()

# Delete a Certificate
cm.Certificate.delete("example-cert", namespace="default")
```

## 📚 Documentation

For complete documentation, visit [cloudcoil.github.io/cloudcoil](https://cloudcoil.github.io/cloudcoil)

## 📜 License

Apache License, Version 2.0 - see [LICENSE](LICENSE)
