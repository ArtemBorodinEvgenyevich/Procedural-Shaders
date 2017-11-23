# Decorative wood

Here are a few renders of the shader. It represents a material that could be used for plastic or natural wood surfaces with a distinctive saw-like pattern.

The settings of the shader allow you control the output albedo color and image-based float information: roughness, specular and displace ammount. Unfortunatelly, Cycles does not support osls' metadata. That's why there might be a little difference with displacement ammount control in .osl/.oso files for different render engines.

# Attention!

The main pattern distribution above the surface was done by Larry Grits' code examples. In this shader I am using vfbm vector. Here is a code example of that vector defined by structure: 

    vector vfBm (point p, float octaves, float lacunarity, float gain)
    {
        float amp = 1;
        point pp = p;
        vector sum = 0;
        float i;

        for (i = 0;  i < octaves;  i += 1) {
            vector d = snoise(pp);
            sum += amp * d;
            amp *= gain;
            pp *= lacunarity;
        }
        return sum;
    }
