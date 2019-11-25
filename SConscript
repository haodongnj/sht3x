from building import *

cwd     = GetCurrentDir()
src     = Glob('*.c')
path    = [cwd]

group = DefineGroup('sht3x', src, depend = ['PKG_USING_SHT3X'], CPPPATH = path)

Return('group')