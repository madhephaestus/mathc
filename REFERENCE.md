# MathC Reference

## Utils

```c
int nearly_equal(float a, float b, float epsilon);
```

Used to compare two `float` variables with an error margin `epsilon`. The standard header `<float.h>` comes with the macro `FLT_EPSILON` that can be used as the error margin. Greater values are also acceptable in most cases, such as `FLT_EPSILON * 10.0f` and `FLT_EPSILON * 100.0f`.

Returns `TRUE` if the values are accepted as equal and `FALSE` otherwise.

```c
float to_radians(float degrees);
```

Return the angle `degrees` in radians.

```c
float to_degrees(float radians);
```

Return the angle `radians` in degrees.

## Vector and Quaternion Structure

Vectors (2D and 3D) and quaternions use the same structure `struct vec`.

```c
struct vec {
	float x;
	float y;
	float z;
	float w;
};
```

## 2D Vector

When using 2D vectors, it is good practice to initialize the variable with `0`, so the value of the `z` component is set to `0.0f`.

Example:

```
struct vec position = {0};
```

The only functions that will set the `z` component of a 2D vector to `0.0f` are `to_pvector2()` and `to_vector2()`. The other operation functions will not change the `z` value, since it's useful when you need to modify yourself.

Every function for 2D vectors will set the value of `w` to `1.0f`.

```c
void to_pvector2(float x, float y, struct vec *result);
struct vec to_vector2(float x, float y);
```

The result is a 2D vector for the position `x` and `y`. The value of `z` is set to `0.0f`.

```c
void pvector2_add(struct vec *a, struct vec *b, struct vec *result);
struct vec vector2_add(struct vec a, struct vec b);
```

The result is a 2D vector for the addition of the 2D vector `a` with the 2D vector `b`.

```c
void pvector2_subtract(struct vec *a, struct vec *b, struct vec *result);
struct vec vector2_subtract(struct vec a, struct vec b);
```

The result is a 2D vector for the subraction of the 2D vector `a` with the 2D vector `b`.

```c
void pvector2_scale(struct vec *a, float scale, struct vec *result);
struct vec vector2_scale(struct vec a, float scale);
```

The result is a 2D vector for the scaling of the 2D vector `a` with the value `scale`.

```c
void pvector2_multiply(struct vec *a, struct vec *b, struct vec *result);
struct vec vector2_multiply(struct vec a, struct vec b);
```

The result is a 2D vector for the multiplication of the 2D vector `a` with the 2D vector `b`.

```c
void pvector2_divide(struct vec *a, struct vec *b, struct vec *result);
struct vec vector2_divide(struct vec a, struct vec b);
```

The result is a 2D vector for the division of the 2D vector `a` with the 2D vector `b`.

```c
void pvector2_negative(struct vec *a, struct vec *result);
struct vec vector2_negative(struct vec a);
```

The result is a 2D vector for the negation of the 2D vector `a`.

```c
void pvector2_inverse(struct vec *a, struct vec *result);
struct vec vector2_inverse(struct vec a);
```

The result is a 2D vector for the inversion of the 2D vector `a`.

```c
void pvector2_abs(struct vec *a, struct vec *result);
struct vec vector2_abs(struct vec a);
```

The result is a 2D vector for the 2D vector `a` with absolute values.

```c
void pvector2_floor(struct vec *a, struct vec *result);
struct vec vector2_floor(struct vec a);
```

The result is a 2D vector for the 2D vector `a` with floored values.

```c
void pvector2_ceil(struct vec *a, struct vec *result);
struct vec vector2_ceil(struct vec a);
```

The result is a 2D vector for the 2D vector `a` with ceiled values.

```c
void pvector2_round(struct vec *a, struct vec *result);
struct vec vector2_round(struct vec a);
```

The result is a 2D vector for the 2D vector `a` with rounded values.

```c
void pvector2_max(struct vec *a, struct vec *b, struct vec *result);
struct vec vector2_max(struct vec a, struct vec b);
```

The result is a 2D vector with the maximum values between the 2D vector `a` and the 2D vector `b`.

```c
void pvector2_min(struct vec *a, struct vec *b, struct vec *result);
struct vec vector2_min(struct vec a, struct vec b);
```

The result is a 2D vector with the minimum values between the 2D vector `a` and the 2D vector `b`.

```c
float pvector2_dot(struct vec *a, struct vec *b);
float vector2_dot(struct vec a, struct vec b);
```

The result is the dot product of the 2D vector `a` with the 2D vector `b`.

```c
float pvector2_angle(struct vec *a);
float vector2_angle(struct vec a);
```

The result is the angle of the 2D vector `a` with the origin.

```c
float pvector2_length_squared(struct vec *a);
float vector2_length_squared(struct vec a);
```

The result is the length squared of the 2D vector `a`.

```c
float pvector2_length(struct vec *a);
float vector2_length(struct vec a);
```

The result is the length of the 2D vector `a`.

```c
void pvector2_normalize(struct vec *a, struct vec *result);
struct vec vector2_normalize(struct vec a);
```

The result is a 2D vector for the normalized 2D vector `a`.

```c
void pvector2_slide(struct vec *a, struct vec *normal, struct vec *result);
struct vec vector2_slide(struct vec a, struct vec normal);
```

The result is a 2D vector for the slided 2D vector `a` against the 2D vector `normal`.

```c
void pvector2_reflect(struct vec *a, struct vec *normal, struct vec *result);
struct vec vector2_reflect(struct vec a, struct vec normal);
```

The result is a 2D vector for the reflected 2D vector `a` against the 2D vector `normal`.

```c
void pvector2_tangent(struct vec *a, struct vec *result);
struct vec vector2_tangent(struct vec a);
```

The result is a 2D vector for the tangent of the 2D vector `a`.

```c
void pvector2_rotate(struct vec *a, float angle, struct vec *result);
struct vec vector2_rotate(struct vec a, float angle);
```

The result is a 2D vector for the rotated 2D vector `a` with the value in radians `angle`.

```c
float pvector2_distance_to(struct vec *a, struct vec *b);
float vector2_distance_to(struct vec a, struct vec b);
```

The result is the distance between the 2D vector `a` and the 2D vector `b`.

```c
float pvector2_distance_squared_to(struct vec *a, struct vec *b);
float vector2_distance_squared_to(struct vec a, struct vec b);
```

The result is the distance squared between the 2D vector `a` and the 2D vector `b`.

```c
void pvector2_linear_interpolation(struct vec *a, struct vec *b, float, p, struct vec *result);
struct vec vector2_linear_interpolation(struct vec a, struct vec b, float p);
```

The result is a 2D vector for the linear interpolation between the 2D vector `a` and the 2D vector `b` with the value `p`.

## 3D Vector

Every function for 3D vectors will set the value of `w` to `1.0f`.

```c
void to_pvector3(float x, float y, float z, struct vec *result);
struct vec to_vector2(float x, float y, float z);
```

The result is a 3D vector for the position `x`, `y` and `z`.

```c
void pvector3_add(struct vec *a, struct vec *b, struct vec *result);
struct vec vector3_add(struct vec a, struct vec b);
```

The result is a 3D vector for the addition of the 3D vector `a` with the 3D vector `b`.

```c
void pvector3_subtract(struct vec *a, struct vec *b, struct vec *result);
struct vec vector3_subtract(struct vec a, struct vec b);
```

The result is a 3D vector for the subraction of the 3D vector `a` with the 3D vector `b`.

```c
void pvector3_scale(struct vec *a, float scale, struct vec *result);
struct vec vector3_scale(struct vec a, float scale);
```

The result is a 3D vector for the scaling of the 3D vector `a` with the value `scale`.

```c
void pvector3_multiply(struct vec *a, struct vec *b, struct vec *result);
struct vec vector3_multiply(struct vec a, struct vec b);
```

The result is a 3D vector for the multiplication of the 3D vector `a` with the 3D vector `b`.

```c
void pvector3_divide(struct vec *a, struct vec *b, struct vec *result);
struct vec vector3_divide(struct vec a, struct vec b);
```

The result is a 3D vector for the division of the 3D vector `a` with the 3D vector `b`.

```c
void pvector3_negative(struct vec *a, struct vec *result);
struct vec vector3_negative(struct vec a);
```

The result is a 3D vector for the negation of the 3D vector `a`.

```c
void pvector3_inverse(struct vec *a, struct vec *result);
struct vec vector3_inverse(struct vec a);
```

The result is a 3D vector for the inversion of the 3D vector `a`.

```c
void pvector3_abs(struct vec *a, struct vec *result);
struct vec vector3_abs(struct vec a);
```

The result is a 3D vector for the 3D vector `a` with absolute values.

```c
void pvector3_floor(struct vec *a, struct vec *result);
struct vec vector3_floor(struct vec a);
```

The result is a 3D vector for the 3D vector `a` with floored values.

```c
void pvector3_ceil(struct vec *a, struct vec *result);
struct vec vector3_ceil(struct vec a);
```

The result is a 3D vector for the 3D vector `a` with ceiled values.

```c
void pvector3_round(struct vec *a, struct vec *result);
struct vec vector3_round(struct vec a);
```

The result is a 3D vector for the 3D vector `a` with rounded values.

```c
void pvector3_max(struct vec *a, struct vec *b, struct vec *result);
struct vec vector3_max(struct vec a, struct vec b);
```

The result is a 3D vector with the maximum values between the 3D vector `a` and the 3D vector `b`.

```c
void pvector3_min(struct vec *a, struct vec *b, struct vec *result);
struct vec vector3_min(struct vec a, struct vec b);
```

The result is a 3D vector with the minimum values between the 3D vector `a` and the 3D vector `b`.

```c
float pvector3_dot(struct vec *a, struct vec *b);
float vector3_dot(struct vec a, struct vec b);
```

The result is the dot product of the 3D vector `a` with the 3D vector `b`.

```c
float pvector3_cross(struct vec *a, struct vec *b);
float vector3_cross(struct vec a, struct vec b);
```

The result is the cross product of the 3D vector `a` with the 3D vector `b`.

```c
float pvector3_length_squared(struct vec *a);
float vector3_length_squared(struct vec a);
```

The result is the length squared of the 3D vector `a`.

```c
float pvector3_length(struct vec *a);
float vector3_length(struct vec a);
```

The result is the length of the 3D vector `a`.

```c
void pvector3_normalize(struct vec *a, struct vec *result);
struct vec vector3_normalize(struct vec a);
```

The result is a 3D vector for the normalized 3D vector `a`.

```c
void pvector3_slide(struct vec *a, struct vec *normal, struct vec *result);
struct vec vector3_slide(struct vec a, struct vec normal);
```

The result is a 3D vector for the slided 3D vector `a` against the 3D vector `normal`.

```c
void pvector3_reflect(struct vec *a, struct vec *normal, struct vec *result);
struct vec vector3_reflect(struct vec a, struct vec normal);
```

The result is a 3D vector for the reflected 3D vector `a` against the 3D vector `normal`.

```c
float pvector3_distance_to(struct vec *a, struct vec *b);
float vector3_distance_to(struct vec a, struct vec b);
```

The result is the distance between the 3D vector `a` and the 3D vector `b`.

```c
float pvector3_distance_squared_to(struct vec *a, struct vec *b);
float vector3_distance_squared_to(struct vec a, struct vec b);
```

The result is the distance squared between the 3D vector `a` and the 3D vector `b`.

```c
void pvector3_linear_interpolation(struct vec *a, struct vec *b, float, p, struct vec *result);
struct vec vector3_linear_interpolation(struct vec a, struct vec b, float p);
```

The result is a 3D vector for the linear interpolation between the 3D vector `a` and the 3D vector `b` with the value `p`.

## Quaternion

```c
void to_pquaternion(float x, float y, float z, struct vec *result);
struct vec to_quaternion(float x, float y, float z);
```

The result is a quaternion for the position `x`, `y` and `z`.

```c
void pquaternion_add(struct vec *a, struct vec *b, struct vec *result);
struct vec quaternion_add(struct vec a, struct vec b);
```

The result is a quaternion for the addition of the quaternion `a` with the quaternion `b`.

```c
void pquaternion_subtract(struct vec *a, struct vec *b, struct vec *result);
struct vec quaternion_subtract(struct vec a, struct vec b);
```

The result is a quaternion for the subraction of the quaternion `a` with the quaternion `b`.

```c
void pquaternion_scale(struct vec *a, float scale, struct vec *result);
struct vec quaternion_scale(struct vec a, float scale);
```

The result is a quaternion for the scaling of the quaternion `a` with the value `scale`.

```c
void pquaternion_multiply(struct vec *a, struct vec *b, struct vec *result);
struct vec quaternion_multiply(struct vec a, struct vec b);
```

The result is a quaternion for the multiplication of the quaternion `a` with the quaternion `b`.

```c
void pquaternion_divide(struct vec *a, struct vec *b, struct vec *result);
struct vec quaternion_divide(struct vec a, struct vec b);
```

The result is a quaternion for the division of the quaternion `a` with the quaternion `b`.

```c
void pquaternion_negative(struct vec *a, struct vec *result);
struct vec quaternion_negative(struct vec a);
```

The result is a quaternion for the negation of the quaternion `a`.

```c
void pquaternion_conjugate(struct vec *a, struct vec *result);
struct vec quaternion_conjugate(struct vec a);
```

The result is a quaternion for the conjugate of the quaternion `a`.

```c
void pquaternion_inverse(struct vec *a, struct vec *result);
struct vec quaternion_inverse(struct vec a);
```

The result is a quaternion for the inversion of the quaternion `a`.

```c
void pquaternion_abs(struct vec *a, struct vec *result);
struct vec quaternion_abs(struct vec a);
```

The result is a quaternion for the quaternion `a` with absolute values.

```c
void pquaternion_floor(struct vec *a, struct vec *result);
struct vec quaternion_floor(struct vec a);
```

The result is a quaternion for the quaternion `a` with floored values.

```c
void pquaternion_ceil(struct vec *a, struct vec *result);
struct vec quaternion_ceil(struct vec a);
```

The result is a quaternion for the quaternion `a` with ceiled values.

```c
void pquaternion_round(struct vec *a, struct vec *result);
struct vec quaternion_round(struct vec a);
```

The result is a quaternion for the quaternion `a` with rounded values.

```c
void pquaternion_max(struct vec *a, struct vec *b, struct vec *result);
struct vec quaternion_max(struct vec a, struct vec b);
```

The result is a quaternion with the maximum values between the quaternion `a` and the quaternion `b`.

```c
void pquaternion_min(struct vec *a, struct vec *b, struct vec *result);
struct vec quaternion_min(struct vec a, struct vec b);
```

The result is a quaternion with the minimum values between the quaternion `a` and the quaternion `b`.

```c
float pquaternion_dot(struct vec *a, struct vec *b);
float quaternion_dot(struct vec a, struct vec b);
```

The result is the dot product of the quaternion `a` with the quaternion `b`.

```c
float pquaternion_angle(struct vec *a, struct vec *b);
float quaternion_angle(struct vec a, struct vec b);
```

The result is the angle between the quaternion `a` and the quaternion `b`.

```c
float pquaternion_length_squared(struct vec *a);
float quaternion_length_squared(struct vec a);
```

The result is the length squared of the quaternion `a`.

```c
float pquaternion_length(struct vec *a);
float quaternion_length(struct vec a);
```

The result is the length of the quaternion `a`.

```c
void pquaternion_normalize(struct vec *a, struct vec *result);
struct vec quaternion_normalize(struct vec a);
```

The result is a quaternion for the normalized quaternion `a`.

```c
void pquaternion_power(struct vec *a, float exponent, struct vec *result);
struct vec quaternion_power(struct vec a, float exponent);
```

The result is a quaternion for the quaternion `a` raised to the exponent `exponent`.

```c
void pquaternion_from_axis_angle(struct vec *a, float angle, struct vec *result);
struct vec quaternion_from_axis_angle(struct vec a, float angle);
```

The result is a quaternion for the 3D vector `a` with the value in radians `angle`.

```c
void pquaternion_rotation_matrix(struct mat *m, struct vec *result);
struct vec quaternion_rotation_matrix(struct mat m);
```

The result is a quaternion for the rotation matrix `m`.

```c
void pquaternion_yaw_pitch_roll(float yaw, float pitch, float roll, struct vec *result);
struct vec quaternion_yaw_pitch_roll(float yaw, float pitch, float roll);
```

The result is a quaternion for the vertical axis `yaw`, the lateral axis `pitch` and the longitudinal axis `roll`.

```c
void pquaternion_linear_interpolation(struct vec *a, struct vec *b, float, p, struct vec *result);
struct vec quaternion_linear_interpolation(struct vec a, struct vec b, float p);
```

The result is a quaternion for the linear interpolation between the quaternion `a` and the quaternion `b` with the value `p`.

```c
void pquaternion_spherical_linear_interpolation(struct vec *a, struct vec *b, float, p, struct vec *result);
struct vec quaternion_spherical_linear_interpolation(struct vec a, struct vec b, float p);
```

The result is a quaternion for the spherical linear interpolation between the quaternion `a` and the quaternion `b` with the value `p`.

## Matrix

```c
void pmatrix_identity(struct mat *result);
struct mat matrix_identity(void);
```

The result is a identity matrix.

```c
void pmatrix_ortho(float l, float r, float b, float t, float n, float f, struct mat *result);
struct mat matrix_ortho(float l, float r, float b, float t, float n, float f);
```

The result is a orthographic projection matrix with the left `l`, right `r`, bottom `b`, top `t`, near distance `n` and far distance `f`.

```c
void pmatrix_perspective_fov(float fov, float aspect, float n, float f, struct mat *result);
struct mat matrix_perspective_fov(float fov, float aspect, float n, float f);
```

The result is a perspective projection matrix with the field of view `fov`, in radians, aspect ratio `aspect`, near distance `n` and far distance `f`.

```c
void pmatrix_perspective(float l, float r, float t, float b, float n, float f, struct mat *result);
struct mat matrix_perspective(float l, float r, float t, float b, float n, float f);
```

The result is a perspective projection matrix with the bountadies set tot hte left `l`, right `r`, top `t`, bottom `b`, near distance `n` and far distance `f`.

```c
void pmatrix_rotation_x(float angle, struct mat *result);
struct mat matrix_rotation_x(float angle);
```

The result is a rotation matrix with radians `angle` on the X axis.

```c
void pmatrix_rotation_y(float angle, struct mat *result);
struct mat matrix_rotation_y(float angle);
```

The result is a rotation matrix with radians `angle` on the Y axis.

```c
void pmatrix_rotation_z(float angle, struct mat *result);
struct mat matrix_rotation_z(float angle);
```

The result is a rotation matrix with radians `angle` on the Z axis.

```c
void pmatrix_rotation_axis(struct vec *a, float angle, struct mat *result);
struct mat matrix_rotation_axis(struct vec a, float angle);
```

The result is a rotation matrix with radians `angle` on the axis of the 3D vector `a`.

```c
void pmatrix_rotation_quaternion(struct vec *q, struct mat *result);
struct mat matrix_rotation_quaternion(struct vec q);
```

The result is a rotation matrix from the quaternion `q`.

```c
void pmatrix_look_at(struct vec *pos, struct vec *target, struct mat *result);
struct mat matrix_look_at(struct vec pos, struct vec target);
```

The result is a view matrix with the position at the 3D vector `pos`, looking at the 3d vector `target`. The up direction is assumed `[0.0f, 1.0f, 0.0f]`.

```c
void pmatrix_scale(struct vec *v, struct mat *result);
struct mat matrix_scale(struct vec v);
```

The result is a scaling matrix for the 3D vector `v`.

```c
void pmatrix_get_scale(struct mat *m, struct vec *result);
struct vec matrix_get_scale(struct mat m);
```

The result is a 3D vector from the scale of the scale matrix `m`.

```c
void pmatrix_translation(struct vec *v, struct mat *result);
struct mat matrix_translation(struct vec v);
```

The result is a translation matrix for the 3D vector `v`.

```c
void pmatrix_get_translation(struct mat *m, struct vec *result);
struct vec matrix_get_translation(struct mat m);
```

The result is a 3D vector from the translation of the translation matrix `m`.

```c
void pmatrix_negative(struct mat *m, struct mat *result);
struct mat matrix_negative(struct mat m);
```

The result is a matrix for the negation of the matrix `m`.

```c
void pmatrix_multiply(struct mat *m, float s, struct mat *result);
struct mat matrix_multiply(struct mat m, float s);
```

The result is a matrix for the multiplication of the matrix `a` with the scale `s`.

```c
void pmatrix_multiply_matrix(struct mat *a, struct mat *b, struct mat *result);
struct mat matrix_multiply_matrix(struct mat a, struct mat b);
```

The result is a matrix for the multiplication of the matrix `a` with the matrix `b`.

```c
void pmatrix_multiply_f4(struct mat *m, float *result);
void matrix_multiply_f4(struct mat m, float *result);
```

Multiply the values of the array `result` with 4 `float` elements by the matrix `m`.

```c
void pmatrix_to_array(struct mat *m, float *result);
void matrix_to_array(struct mat m, float *result);
```

Copy the elements of the matrix `m` to the array `result` with 16 `float` elements.

## Easing Functions

```c
float quadratic_ease_in(float p);
float quadratic_ease_out(float p);
float quadratic_ease_in_out(float p);
float cubic_ease_in(float p);
float cubic_ease_out(float p);
float cubic_ease_in_out(float p);
float quartic_ease_in(float p);
float quartic_ease_out(float p);
float quartic_ease_in_out(float p);
float quintic_ease_in(float p);
float quintic_ease_out(float p);
float quintic_ease_in_out(float p);
float sine_ease_in(float p);
float sine_ease_out(float p);
float sine_ease_in_out(float p);
float circular_ease_in(float p);
float circular_ease_out(float p);
float circular_ease_in_out(float p);
float exponential_ease_in(float p);
float exponential_ease_out(float p);
float exponential_ease_in_out(float p);
float elastic_ease_in(float p);
float elastic_ease_out(float p);
float elastic_ease_in_out(float p);
float back_ease_in(float p);
float back_ease_out(float p);
float back_ease_in_out(float p);
float bounce_ease_in(float p);
float bounce_ease_out(float p);
float bounce_ease_in_out(float p);
```

Each easing function will return a rate of change for `p`. The value of `p` must be inside the range `0.0f-1.0f`.

The graphic visualization of the easing functions can be found on [easing.net](http://easings.net/).

# LICENSE

The source code of this project is licensed under the terms of the ZLIB license:

Copyright (C) 2016 Felipe Ferreira da Silva

This software is provided 'as-is', without any express or implied warranty. In no event will the authors be held liable for any damages arising from the use of this software.

Permission is granted to anyone to use this software for any purpose, including commercial applications, and to alter it and redistribute it freely, subject to the following restrictions:

1. The origin of this software must not be misrepresented; you must not claim that you wrote the original software. If you use this software in a product, an acknowledgment in the product documentation would be appreciated but is not required.
2. Altered source versions must be plainly marked as such, and must not be misrepresented as being the original software.
3. This notice may not be removed or altered from any source distribution.
