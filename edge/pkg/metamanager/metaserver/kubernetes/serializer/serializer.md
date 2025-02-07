
## Test Plan for serializer Package

1. NewNegotiatedSerializer() Function
Ensure NewNegotiatedSerializer() returns a valid runtime.NegotiatedSerializer.
Verify that the returned serializer supports both JSON and YAML media types.
Check that the creator and typer are properly initialized using unstructuredscheme.
2. WithoutConversionCodecFactory Struct
SupportedMediaTypes() Method

Ensure it returns a list of media types: "application/json" and "application/yaml".
Validate that each media type has the correct serializer settings:
JSON supports Pretty, Strict, and Streaming serializers.
YAML serializer uses json.SerializerOptions{Yaml: true}.
EncoderForVersion() Method

Ensure it wraps the given encoder in SetVersionEncoder.
Validate that the Version field is set correctly.
DecoderToVersion() Method

Ensure it returns the provided decoder without modifications.
3. SetVersionEncoder Struct
Identifier() Method

Verify that it returns a string containing "SetVersionEncoder:" followed by the version identifier.
Encode() Method

Check that it properly encodes the given object using the underlying encoder.
If WithKindGroupVersioner is used, ensure it sets the object's GroupVersionKind before encoding.
4. AdapterDecoder Struct
Decode() Method
Ensure it correctly decodes objects from byte data.
When decoding fails but a GroupVersionKind is provided, verify that defaults is updated accordingly.
5. WithKindGroupVersioner Struct
KindForGroupVersionKinds() Method

Validate that it always returns the embedded GroupVersionKind.
Ensure ok is always true.
Identifier() Method

Verify it returns the string representation of the GroupVersionKind.
NewWithKindGroupVersioner() Function

Ensure it initializes and returns a valid WithKindGroupVersioner instance